<template>
    <div class="my-component pb-56 pt-56">
        <h1 class="text-3xl mb-6 text-center">Hitung Total</h1>
        <div class="flex justify-center mb-5">
        <div class="w-full max-w-sm">
            <p class="text-center">Masukan Total Harga :</p>
            <div class="flex justify-center items-center border-b border-teal-500 py-2">
                <input v-model="harga"
                    class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none"
                    type="number" placeholder="Input Jumlah Harga" aria-label="Full name" />
                <button
                    class="flex-shrink-0 bg-teal-500 hover:bg-teal-700 border-teal-500 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded"
                    type="button" @click="hitungdiscount(harga)">
                    Hitung
                </button>
            </div>
        </div>
        </div>
        <div class="flex justify-center items-center">
            <div v-show="total">
                <table>
                    <tbody>
                        <tr>
                            <td class="p-2 align-top">Subtotal</td>
                            <td class="p-2 align-top">:</td>
                            <td class="p-2 align-top text-right">
                                Rp. {{ (harga).toLocaleString() }}
                            </td>
                        </tr>
                        <tr>
                            <td class="p-2 align-top">Discount</td>
                            <td class="p-2 align-top">:</td>
                            <td class="p-2 align-top text-right">
                                {{ Math.round(discount * 100) + "%" }}
                            </td>
                        </tr>
                        <tr>
                            <td class="p-2 align-top">Potongan</td>
                            <td class="p-2 align-top">:</td>
                            <td class="p-2 align-top text-right">
                                Rp. {{ (harga*discount).toLocaleString() }}
                            </td>
                        </tr>
                        <tr>
                            <td class="p-2 align-top border-t-2">Total</td>
                            <td class="p-2 align-top border-t-2">:</td>
                            <td class="p-2 align-top border-t-2 text-right"><strong>Rp. {{ total.toLocaleString() }} </strong></td>
                        </tr>
                    </tbody>    
                </table>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    name: "card",
    data() {
        return {
            harga: 0,
            total: 0,
            discount: 0,
        };
    },
    methods: {
        hitungdiscount(num) {
            if (num >= 100000) {
                this.discount = 0.1;
            } else if (num >= 50000) {
                this.discount = 0.05;
            } else {
                this.discount = 0.0;
            }

            this.total = num - num * this.discount;
        },
    },
};
</script>
  
<style scoped></style>
  