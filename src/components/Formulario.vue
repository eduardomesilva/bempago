<template>
   <div class="common-layout">
    <el-container>
       <el-main>
        <el-row class="row-bg">
            <h3>Compre Adesivos Rápido e Facíl</h3>
            <el-col>
                <h3>Valor Unitario dos Adesivos R$ 5.00</h3>
            </el-col>
        </el-row>
            <el-col>
                <h3> Escolha qual adesivo comprar</h3>
            </el-col>

            <div>
                <el-col> <el-checkbox-button v-model="vue" label="Veu.js" size="large" /> </el-col>
                <el-col> <el-checkbox-button v-model="react" label="React" size="large" /> </el-col>
                <el-col> <el-checkbox-button v-model="angular" label="Angular" size="large" /> </el-col>
            </div>
            <el-row class="row-bg" justify="center">
                <h3> Informe a quantidade de adesivos </h3>
            </el-row>
            <el-row>
                <el-col>
                    <el-input-number v-model="num" @change="handleChange"  size="large" />
                </el-col>
            </el-row>
            <el-row class="row-bg" justify="center">
                <el-col :span="6">
                    <el-input 
                        v-model="textArea"
                        :rows="4"
                        type="textarea"
                        background="grey"
                        placeholder="Alguma duvida?"
                    />
                </el-col>
            </el-row>
            <el-button type="success">Enviar</el-button>
            <el-row class="row-bg" justify="center">
                <el-col>
                    <h3>Formas de Pagamentos</h3>
                </el-col>
                <el-col>
                    <el-checkbox-button v-model="cartao" label="Cartão" size="large" />
                    <el-checkbox-button v-model="boleto" label="Boleto" size="large" /> 
                    <el-checkbox-button v-model="pix" label="Pix" size="large" /> 
                </el-col>
            </el-row>
            <el-col>
                <el-button :span="6" @click="formaPagamentoCartao" type="success">Finalizar Compra</el-button>
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
                    <el-button type="success">Pagar</el-button>
                </el-col>
                </el-row>
                <el-row class="row-bg" justify="center" v-show="pagarPix">
                <h1>Aqui vai o qrcode</h1>
                </el-row>
                <el-row class="row-bg" justify="center" v-show="pagarBoleto">
                <h1>Olá senhor {{orde.nome}}, o boleto foi enviado para seu email, obrigado pela compra</h1>
                </el-row>
            </el-main>
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
                let valor
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
  border: 10px;
  background-color: 
}
.el-row {
  margin-bottom: 25px;
}
.el-col {
  margin-bottom: 25px;
}

.common-layout{
  background-color: #E6E6FA;
}
.el-header {
    background-color: #F0FFFF;
}

.el-checkbox-button{
    margin-left: 10px;
    border: 110px;
}


</style>