<template>
   <div class="common-layout">
    <el-container>
      <el-header>
        <h1> Formulario para compra de pacotes de adesivos</h1>
        <Pagamento></Pagamento>
      </el-header>
      <el-main>
        <span> Escolha qual adesivo comprar</span>
        <div>
            <el-checkbox v-model="checked1" label="Veu.js" size="large" />
            <el-checkbox v-model="checked2" label="React" size="large" />
            <el-checkbox v-model="checked3" label="Angular" size="large" />
        </div>
        <span> Informe a quantidade de adesivos </span>
        <div>
            <el-input-number v-model="num" @change="handleChange" />
        </div>
        <div>
            <el-input
                v-model="textarea"
                :rows="2"
                type="textarea"
                placeholder="Please input"
            />
        </div>
        <div>
            <el-button type="success" plain>Success</el-button>
        </div>
      </el-main>
      <el-footer>Footer</el-footer>
    </el-container>
  </div>
</template>

<script>
import { method } from 'lodash'
import Pagamento from './Pagamento.vue'

export default {
    name: "Formulario",
    data() {
        return {
            num: 0
        };
    },
    components: { Pagamento }
}
</script>


<style scoped>

</style>