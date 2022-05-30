
<template>
<h1><i class="text-slate-50 fa-solid fa-plus fa-xl mr-4"></i></h1>
    <h1 v-if="ex">{{sapa}}</h1>
    <h1 v-else class="mb-5">kosong</h1>
    <button @click="func">ubah</button>
    <ul v-for="(arrs,index) in arr" key="index" class="mt-5">
        <li>{{arrs.nama}}</li>
        <li>{{arrs.umur}}</li>
    </ul>
    <button @click="delt">hapus</button>
</template>


<script>
    export default {
        props:[
            'sapa'
        ],
        data(){
            return{
                ex:'true',
                arr:[
                        {
                            nama:'andhika',
                            umur:'21',
                        },
                        {
                            nama:'bambang',
                            umur:'41',
                        },
                        {
                            nama:'dosy',
                            umur:'12',
                        },
                        {
                            nama:'makmur',
                            umur:'72',
                        }
                    ]
            }
        },
        methods:{
            func(){
                this.ex = !this.ex
            },
            delt(){
                this.arr.splice(-1)
            }
        }
    }
</script>