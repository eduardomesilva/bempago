<template>
   <div class="common-layout">
    <el-container>
      <el-header>
        <h1> Compre adesivos rápido e facíl</h1>
      </el-header>
    <el-container>
        <el-aside width="600px">Aside
            <el-main>
                <el-col>
                    <span> Escolha qual adesivo comprar</span>
                    {{quantidade}}
                </el-col>
                <div>
                    <el-col> <el-checkbox v-model="vue" label="Veu.js" size="large" /> </el-col>
                    <el-col> <el-checkbox v-model="react" label="React" size="large" /> </el-col>
                    <el-col> <el-checkbox v-model="angular" label="Angular" size="large" /> </el-col>
                </div>
                <el-row class="row-bg" justify="center">
                    <span> Informe a quantidade de adesivos </span>
                </el-row>
                <el-row>
                    <el-col>
                        <el-input-number v-model="num" @change="handleChange" />
                    </el-col>
                </el-row>
                <el-row class="row-bg" justify="center">
                    <el-col :span="12">
                        <el-input 
                            v-model="textArea"
                            :rows="4"
                            type="textarea"
                            background="grey"
                            placeholder="Alguma duvida?"
                        />
                    </el-col>
                </el-row>
                 <el-button type="success" plain>Enviar</el-button>
                <el-row>
                </el-row>
            </el-main>
        </el-aside>
        <el-container>
            <el-main>
                <el-row class="row-bg" justify="center">
                    <a>Formas de Pagamentos</a>
                </el-row>
                <div>
                    <el-checkbox v-model="cartao" label="Cartão" size="large" />
                    <el-checkbox v-model="boleto" label="Boleto" size="large" /> 
                    <el-checkbox v-model="pix" label="Pix" size="large" /> 
                </div>
                <el-col>
                    <el-button @click="formaPagamentoCartao" type="success" plain>Comprar</el-button>
                </el-col>
                <el-row class="row-bg" justify="center" v-show="pagarCartao">
                    <el-col :span="8">
                        <div class="pag">
                            <div class="client">
                                <el-input v-model="orde.nome" placeholder="Nome" />
                                <el-input v-model="orde.sobrenome" placeholder="Sobrenome" />
                                <el-input v-model="orde.cpf" placeholder="CPF" />
                                <el-input v-model="orde.email" placeholder="email" />
                                <el-input v-model="orde.numero_cartao" placeholder="Numero do cartão" />
                                <el-col :span="4">
                                    <el-input v-model="orde.data_validade" placeholder="validade"/>
                                    <el-input v-model="orde.cvv" maxlength="3" placeholder="CVV" />
                                </el-col>
                            </div>
                        </div>
                    </el-col>
                    <el-col>
                        <el-button type="success" plain>Pagar</el-button>
                    </el-col>
                </el-row>
                <el-row class="row-bg" justify="center" v-show="pagarPix">
                <h1>Aqui vai o qrcode</h1>
                </el-row>
                <el-row class="row-bg" justify="center" v-show="pagarBoleto">
                <h1>Aqui vai o Boleto</h1>
                </el-row>
            </el-main>
            <el-footer>Footer</el-footer>
        </el-container>
    </el-container>
    </el-container>
  </div>
</template>

<script>
import { method } from 'lodash'

export default {
    name: "Formulario",
    data() {
        return {
            quantidade: 0,
            valorAdesivos: 5,
            textArea:'',
            num: 0,
            orde :{ 
                nome:'',
                sobrenome:'',
                email:'',
                numero_cartao:'',
                data_validade:'',
                cvv:'',
                cpf:''
            },
            cartao: true,
            pix: true,
            boleto: true,
            pagarCartao: true,
            pagarPix: true,
            pagarBoleto: true,
            vue: true,
            react: true,
            angular: true,
        };
    },

    methods: {
        compraAdesivos: function(){
            if(this.vue === true || this.react === true || this.angular == true){
                this.quantidade = this.num * this.valorAdesivos
                }
             
        },
        formaPagamentoCartao: function(){
            if(this.cartao === true){
              this.pagarCartao = true
            }
            if(this.pix === true){
              this.pagarPix = true
            }
            if(this.boleto === true){
              this.pagarBoleto = true
            }
        },

    },

    mounted:function(){
        this.pagarCartao = false
        this.vue = false
        this.react = false,
        this.angular = false
        this.cartao= false,
        this.pix=false,
        this.boleto= false,
        this.pagarPix = false,
        this.pagarBoleto = false
    }
}
</script>


<style scoped>
.el-input {
    margin-top: 10px;
}
.el-aside{
  
}
.el-row {
  margin-bottom: 25px;
}
.el-col {
  margin-bottom: 25px;
}
.el-main { 
 
}
.common-layout{
  background-color: azure;
}
.el-header {

}

</style>