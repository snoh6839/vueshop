<template>
    <!-- 모달 -->

    <div class="modalOuterBg" v-if="modalFlag">
        <button class="modalBtn" @click="$emit('closeModal');">X</button>
        <div class="modalInnerBg">
            <div class="valign">
                <img :src="products[proNum].img" alt="" style="width:300px; height: 180px;">
                <h4>상품명 : <span>{{ products[proNum].name }}</span></h4>
                <p>가격 : <span>{{ products[proNum].price }}</span></p>
                <p>{{ products[proNum].contents }}</p>
                <p>count : <input type="text" v-model="inputCount"></p>
                <p>total price : <span>{{ products[proNum].price * inputCount }}</span></p>
            </div>
        </div>
    </div>


</template>

<script>



export default {
    
        name: 'Modal',
        props: {
            modalFlag: Boolean,
            products: Array,
            proNum: Number,
        },
        data() {
        return {
            inputCount: ' ',
        }
    },
    watch: {
        inputCount(input) {
            if (input < 0 || input > 10) {
                alert('1~10 사이 숫자만 입력해 주세요');
                this.inputCount = '10';
            }
        }
    },
    
    
}
</script>