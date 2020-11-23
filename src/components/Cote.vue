<template>
    <v-row>
        <v-col>
        </v-col>
    </v-row>
</template>
<script>
    // console.log('cote');
    //
    // const N = 8;
    // const W = 0;
    // const P = 1;
    // const V = 2;
    // const map = [
    //     [P, W, W, W, W, W, W, P],
    //     [W, P, P, W, W, P, W, W],
    //     [P, P, W, W, P, W, P, W],
    //     [W, W, W, W, W, P, W, W],
    //     [W, P, W, P, W, P, W, W],
    //     [W, P, W, P, W, P, W, W],
    //     [P, W, W, W, P, W, W, P],
    //     [W, P, P, W, W, P, P, P]
    // ];
    // // const visitedArr = new Array(N).fill(0).map(() => new Array(N).fill(0));
    // // console.log('arr', arr);
    //
    //
    // function countCells(x, y) {
    //     if (x < 0 || y < 0 || x > N-1 || y > N-1)
    //         return 0;
    //     else
    //     if (map[x][y] !== P)
    //         return 0;
    //     else {
    //         map[x][y] = V;
    //         return (1 +
    //             countCells(x    , y - 1) +
    //             countCells(x + 1, y - 1) +
    //             countCells(x + 1, y    ) +
    //             countCells(x + 1, y + 1) +
    //             countCells(x    , y + 1) +
    //             countCells(x - 1, y + 1) +
    //             countCells(x - 1, y    ) +
    //             countCells(x - 1, y - 1)
    //         );
    //     }
    // }
    //
    // const result = countCells(5, 3);
    // console.log('result', result);

    //backtracking recursion
    // function backRecursion()
    // {
    //     // if infeasible
    //     // report fail return false
    //     // else if success
    //     // report success return true
    //     // else
    //     // visit children recursively
    // }

    // const M = 4;
    // const cols = new Array(M + 1).fill(0);
    // function queens(level) {
    //     if (! promising(level))
    //         return false;
    //     else
    //     if (level === M){
    //         for (let i = 1; i <= N; i++)
    //             console.log('i: ', i, 'cols', cols[i]);
    //         return true;
    //     }
    //     for (let i = 1; i <= M; i++) {
    //         cols[level + 1] = i;
    //         if (queens(level + 1))
    //             return true;
    //     }
    //     return false;
    // }
    //
    // function promising(level) {
    //     for (let i = 1; i <= level; i++) {
    //         if (cols[i] === cols[level])
    //             return false;
    //         else if (level - i === Math.abs(cols[level] - cols[i]))
    //             return false;
    //     }
    //
    //     return true;
    // }
    //
    // console.log('queens', queens(0));

    const data = ['a', 'b', 'c', 'd', 'e', 'f'];
    const N = data.length;
    const includee = new Array(N).fill(0);
    let count = 0;

    function powerSets(k){
        // s 가 공집합이면
        // print p
        // s 가 공집합이 아니면
        // s 에서 t를 제외하고 모든 부분집합 subset 구하고
        // t를 제외하고 subset 출력 powerSet(P, S-{t});
        // t를 포함하고 subset 출력 powerSet(P U t, S-{t});
        if (k === N) {
            let str = '';
            for (let i = 0; i < N; i++)
                if (includee[i])
                    str += data[i] + " ";

            console.log(str);
            count++;
            return;
        }

        includee[k] = 0;
        powerSets(k + 1);
        includee[k] = 1;
        powerSets(k + 1);
    }

    powerSets(0);
    console.log('count', count);

    function mergeSort(arr, p, r) {
        if (p < r) {
            let q = (p + r) / 2;
            mergeSort(arr, p, q);
            mergeSort(arr, q + 1, r);
            merge(arr, p, q, r);
        }
    }

    function merge(arr, p, q, r) {
        let i = p, j = q + 1, k = p;
        const tmp = new Array(arr.length).fill(0);
        while (i <= q && j <= r){
            if (data[i] <= data[j])
                tmp[k++] = data[i++];
            else
                tmp[k++] = data[j++];
        }
        while(i <= q)
            tmp[k++] = data[i++];
        while(j <= r)
            tmp[k++] = data[j++];

        for(i = p; i <= r; i++)
            data[i] = tmp[i];
    }
    mergeSort();

    export default {
        name: 'Cote',
        // data: () => ({
        //     buttonItems: ['x-small', 'small', 'default', 'large', 'x-large']
        // }),
        computed: {
        }
    }
</script>
<style>

</style>
