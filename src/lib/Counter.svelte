<script>
    const images = [
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/arts/ballet.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/arts/upright.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/fairy-tale/king.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/fairy-tale/sage.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/surfing-js.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/mistake.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/power-to-the-linux.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/power-to-the-mac.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/rocket.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/scientist.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/science/soldering.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/friends/crash-dummy.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/friends/heart-hug.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/friends/liberty.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/friends/stovepipe-hat.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/wwgl.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/vim-go.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/with-C-book.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/surfing-js.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/network.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/network-side.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/projects/emacs-go.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/fairy-tale/witch-learning.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/fairy-tale/witch-too-much-candy.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/fairy-tale/knight.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/computer/gamer.svg",
        "https://raw.githubusercontent.com/egonelbre/gophers/63b1f5a9f334f9e23735c6e09ac003479ffe5df5/vector/computer/music.svg",
    ];
    const matrixSize = 5;
    const N = matrixSize * matrixSize;

    let imgMatrix = [...Array(matrixSize)].map((e) => Array(matrixSize));
    const randImg = images[Math.floor(Math.random() * images.length)];

    const randIndex = Math.floor(Math.random() * N);
    const row = Math.floor(randIndex / matrixSize);
    const col = randIndex % matrixSize;

    imgMatrix[row][col] = randImg;

    for (let row = 0; row < matrixSize; row++) {
        for (let col = 0; col < matrixSize; col++) {
            if (!imgMatrix[row][col]) {
                imgMatrix[row][col] =
                    images[Math.floor(Math.random() * images.length)];
            }
        }
    }
    let found = false;
    const start = Date.now();
    let foundAt = Date.now();

    const selectImgBox = (row, col) => {
        console.log(
            `selected row:${row} col:${col} correct:${
                randImg === imgMatrix[row][col]
            }`
        );

        found = randImg === imgMatrix[row][col];
        if (found) {
            foundAt = Date.now();
        }
    };
</script>

{#if found}
    <div>Congras! You have found it in {foundAt - start}ms</div>
{:else}
    <span>
        Find this gopher ==>>
        <img class="rand-img" src={randImg} alt="" />
    </span>
    <br />
    <br />
    <br />
    <table>
        {#each imgMatrix as row, i}
            <tr>
                {#each row as col, j}
                    <td>
                        <img
                            src={imgMatrix[i][j]}
                            alt=""
                            on:mouseup={() => {
                                selectImgBox(i, j);
                            }}
                        />
                    </td>
                {/each}
            </tr>
        {/each}
    </table>
{/if}

<style>
    .rand-img {
        margin: 5px;
        width: 100px;
        height: 100px;
    }
    td {
        margin: 5px;
        width: 50px;
        height: 50px;
        border: 5px solid transparent;
    }
    td:hover {
        border: 5px solid #333333;
        overflow: hidden;
    }
    img {
        width: 100%;
        height: 100%;
    }
</style>
