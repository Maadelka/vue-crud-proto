<template>
<div class="w-11/12 border-[1px] mx-auto mt-3 rounded-lg pb-2">

    <h1 class="pl-2 pt-2 font-semibold text-slate-50">Daftar barang</h1>

    <table class=" shadow-lg">
        <thead class="bg-slate-800 text-white">
            <tr class="border-[1px]">
                <td class="border-[1px] text-center px-2">No</td>
                <td class="border-[1px] text-center">Nama Barang</td>
                <td class="border-[1px] text-center">Harga</td>
                <td class="border-[1px] text-center">ubah</td>
            </tr>
        </thead>
        <tbody class="bg-slate-500">
            <tr v-for="(barang,index) in daftarBarang" key="index" >
                <td class="border-[1px] px-2 text-center">{{index + 1}}</td>
                <td class="border-[1px] px-2">{{barang.nama}}</td>
                <td class="border-[1px] px-2">{{barang.harga}}</td>
                <td class="border-[1px] px-2">
                    <div class="flex">
                        <p class="hover:text-slate-50 cursor-pointer px-1" @click="edit(index)">edit</p> | <p class="hover:text-slate-50 cursor-pointer px-1" @click="hapuss(index)">remove</p>
                    </div>
                </td>
            </tr>
        </tbody>
    </table>
    <div class=" w-fit flex">
        <p class="bg-slate-700 px-1 font-semibold inline-block  cursor-pointer hover:bg-slate-500" @click="tampilPopup">{{btnValue}}</p>
    </div>

    <div class="border-[1px] w-fit bg-slate-400 content-center flex items-center" v-if="btnt">
        <div class="">
            <label for="nama" class="px-1">Nama Barang</label>
            <input type="text" name="" id="nama" placeholder="nama barang" class="bg-zinc-300 w-60" v-model="nama">
        </div>
        <div class="">
            <label for="harga" class="px-1">Harga Barang</label>
            <input type="text" name="" id="harga" placeholder="harga" class="bg-zinc-300" v-model="harga" >
        </div>
        <button class="bg-slate-700 px-1 hover:bg-slate-600" @click="add" v-if="tambah">tambahkan</button>
        <button class="bg-slate-700 px-1 hover:bg-slate-600" @click="addedit()" v-else-if="updateData">update</button>
    </div>
    <p class="text-red-700 italic" v-if="isiData">masukkan data barang terlebih dahulu!</p>
    

 


    <button @click="console">console.log</button>




</div>
</template>



<script>
import { Input } from 'postcss'
export default{
    data(){
        return{
            ex:'hello world!',
            daftarBarang:[
                {nama:'minyak goreng kemasan',harga:'20.000/1 liter'},
                {nama:'sabun ekonomi',harga:'7.000'},
                {nama:'mie goreng sedap',harga:'3.000'},
                {nama:'indome kari',harga:'3.000'},
                {nama:'telur ayam brass ',harga:'2.000/butir'}
            ],
            btnt: false,
            nama: '',
            harga: '',
            isiData: false,
            btnValue: 'tambahkan',
            updateData: false,
            tambah:false,
            cname: document.getElementById('nama'),
            index: ''
        }
    },
    methods:{
        add(){
            if(this.nama == '' || this.harga == ''){
                this.isiData = true
            }else{
                this.daftarBarang.unshift(
                {
                    nama: this.nama,
                    harga: this.harga
                }
                )
                this.btnt = !this.btnt
                this.nama = ''
                this.harga = ''
                this.isiData = false
                this.btnValue = 'tambahkan'
            }
            
        },
        tampilPopup(){
            this.tambah = true
            this.btnt = !this.btnt
            this.isiData = false
            if(!this.btnt){
                this.btnValue='tambahkan'
                this.nama = ''
                this.harga = ''
            }else{
                this.btnValue='batalkan'
            }
        },
        // tombol remove di click
        hapuss(i){
            // alert(i)
            this.daftarBarang.splice(i,1)
        },
        // tombol edit di click 
        edit(i){
            this.btnValue='batalkan'
            this.btnt = !this.btnt
            this.tambah = false
            this.updateData = true
            // value dimasukkan ke input
            this.nama = this.daftarBarang[i].nama
            this.harga= this.daftarBarang[i].harga
            this.index= i
        },
        // button update di click 
        addedit(){
            this.btnValue='tambahkan'
            this.btnt = !this.btnt
            this.daftarBarang[this.index].nama = this.nama
            this.daftarBarang[this.index].harga = this.harga
            this.nama = ''
            this.harga = ''
        },
        // debug
        console(){
            console.log(this.daftarBarang)
        }
    }
}
</script>