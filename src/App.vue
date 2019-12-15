<template>
  <div id="app">

    <button v-on:click="iniciaPopulacao()" v-if="cond===0">Gerar semana</Button>
    <button v-on:click="AlgoritmoGenético()"  v-if="cond===2">Ativar algoritmo genetico</Button>

    <h1 v-if="cond===2"><p>Tabela de Horários aleatóriamente gerada</p></h1>
    <imprimeData2 v-if="cond===2" v-bind:professores="professores"></imprimeData2>
    <h1  v-if="cond===2">Turma 1</h1>
    <imprimeMatriz2 v-if="cond===2" v-bind:mat="populacao[0].turma[0].week"></imprimeMatriz2>
    <h1  v-if="cond===2">Turma 2</h1>
    <imprimeMatriz2 v-if="cond===2" v-bind:mat="populacao[0].turma[1].week"></imprimeMatriz2>
    <h1  v-if="cond===2">Turma 3</h1>
    <imprimeMatriz2 v-if="cond===2" v-bind:mat="populacao[0].turma[2].week"></imprimeMatriz2>
    <h1  v-if="cond===2">Turma 4</h1>
    <imprimeMatriz2 v-if="cond===2" v-bind:mat="populacao[0].turma[3].week"></imprimeMatriz2>
    <h1  v-if="cond===2">Turma 5</h1>
    <imprimeMatriz2 v-if="cond===2" v-bind:mat="populacao[0].turma[4].week"></imprimeMatriz2>
    


    <h1 v-if="cond===1"><p>Tabela de Horários genéticamente modificada</p></h1>
    <imprimeData v-if="cond===1" v-bind:professores="professores"></imprimeData>
    <br> <h1  v-if="cond===1">Turma 1</h1> <br>
    <imprimeMatriz v-if="cond===1" v-bind:mat="melhorIndividuo[0].turma[0].week"></imprimeMatriz>
    <br> <h1 v-if="cond===1">Turma 2</h1> <br>
    <imprimeMatriz v-if="cond===1" v-bind:mat="melhorIndividuo[0].turma[1].week"></imprimeMatriz>
    <br>  <h1 v-if="cond===1">Turma 3</h1> <br>
    <imprimeMatriz v-if="cond===1" v-bind:mat="melhorIndividuo[0].turma[2].week"></imprimeMatriz>
    <br> <h1 v-if="cond===1">Turma 4</h1> <br>
    <imprimeMatriz v-if="cond===1" v-bind:mat="melhorIndividuo[0].turma[3].week"></imprimeMatriz>
    <br>  <h1 v-if="cond===1">Turma 5</h1> <br>
    <imprimeMatriz v-if="cond===1" v-bind:mat="melhorIndividuo[0].turma[4].week"></imprimeMatriz>
    
    <br><br><br>
    <section class="container">
      <div v-if="cond===1" class="left-half">
       <article>
           <h1>Primeira Geração</h1>
            <imprimeScore  v-bind:primeira="primeriageracao"></imprimeScore> 
        </article>
      </div>
      <div v-if="cond===1" class="right-half">
        <article>
           <h1>Última Geração</h1>
          <imprimeScore2  v-bind:ultima="ultimageracao"></imprimeScore2> 
         </article>
     </div>
    </section>
    


  </div>
</template>

<script>
import imprimeMatriz from './components/imprimeMatriz.vue'
import imprimeMatriz2 from './components/imprimeMatriz2.vue'
import imprimeData from './components/imprimeData.vue'
import imprimeData2 from './components/imprimeData2.vue'
import imprimeScore from './components/imprimeScore.vue'
import imprimeScore2 from './components/imprimeScore2.vue'


export default {
  name: 'app',
  components: {
    imprimeMatriz,
    imprimeMatriz2,
    imprimeData,
    imprimeData2,
    imprimeScore,
    imprimeScore2
  },

  data() {
    return {
      cond:0,
      melhorIndividuo: [],
      populacao:[],
      primeriageracao: [],
      ultimageracao: [],
       professores: [{nome:'Felipe Carbone', id:1, ch: 0},
                       {nome:'Valguima Odakura',id:2, ch: 0},
                       {nome:'Marcos Furlan', id:3, ch: 0},
                       {nome:'Silvana Melo', id:4, ch: 0},
                       {nome:'Marcos Paulo Moro', id:5, ch: 0},
                       {nome:'Rodrigo Sacchi', id:6, ch: 0},
                       {nome:'Willian Paraguassu', id:7, ch: 0},
                       {nome:'Carlos Zampieri', id:8, ch: 0},
                       {nome:'Alfred Forster', id:9, ch: 0},
                       {nome:'Alexandre Szabo', id:10, ch: 0}],
      /*cursos:[{nome:'INTELIGÊNCIA ARTIFICIAL', id:1, ch:72},
             {nome:'REDES DE COMPUTADORES', id:2, ch:72},
             {nome:'SISTEMAS DISTRIBUÍDOS',id:3, ch:72},
             {nome:'SISTEMAS OPERACIONAIS I', id:4, ch:72},
             {nome:'TECNOLOGIA E COMUNICAÇÃO DE DADOS', id:5, ch:72},
             {nome:'PROGRAMAÇÃO ORIENTADA A OBJETOS', id: 6, ch:72},
             {nome:'MÉTODOS NUMÉRICOS PARA COMPUTAÇÃO', id:7, ch:72},
             {nome:'ALGORITMOS E ESTRUTURAS DE DADOS I', id:8, ch:72},
             {nome:'ALGORITMOS E ESTRUTURAS DE DADOS II', id:9, ch:72},
             {nome:'ALGORITMOS E ESTRUTURAS DE DADOS III', id:10, ch:72},
             {nome:'COMPUTAÇÃO E SOCIEDADE',id:11, ch:72},
             {nome:'DESENHO POR COMPUTADOR',id:12, ch:72},
             {nome:'MICROCONTROLADORES E APLICAÇÕES',id:13, ch:72},
             {nome:'TÓPICOS EM SISTEMAS DE INFORMAÇÃO',id:14, ch:72},
             {nome:'VERIFICAÇÃO, VALIDAÇÃO E TESTES DE SOFTWARE',id:15, ch:72},
             {nome:'CIRCUITOS ELETRÔNICOS',id:16, ch:72},
             {nome:'ANÁLISE DE ALGORITMOS',id:17, ch:72},
             {nome:'ANÁLISE DE CIRCUITOS ELÉTRICOS',id:18, ch:72},
             {nome:'ANÁLISE DE SINAIS E SISTEMAS',id:19, ch:72},
             {nome:'EMPREENDEDORISMO',id:20, ch:72}], */
    }
  },

  methods: {
    iniciaPopulacao(){
      var i;
      for(i=0;i<100;i++){
      this.populacao.push({turma:this.generateSemana()});
      }
      this.primeriageracao = this.populacao;
      this.cond=2;
      this.CHprofessor();
    },

    CHprofessor(){
      var k,i,j;
      
      //reinicia CH de todos os professores antes de calcular
      for(k=0;k<10;k++){//percorre lista de professores
        this.professores[k].ch = 0
      }

      if(this.cond === 2){ //calcula ch de professores do individuo inciial 
        for(k=0;k<10;k++){//percorre lista de professores
        for(i=0;i<=4;i++){
          for(j=0;j<16;j++){//percorre semana/dias
          if(this.populacao[0].turma[i].week[j].prof===k){
            this.professores[k].ch = this.professores[k].ch + 2
            }
          }
        }
      }
      } else{

      //calcula ch semanal total do professor
      for(k=0;k<10;k++){//percorre lista de professores
        for(i=0;i<=4;i++){
          for(j=0;j<16;j++){//percorre semana/dias
          if(this.melhorIndividuo[0].turma[i].week[j].prof===k){
            this.professores[k].ch = this.professores[k].ch + 2
            }
          }
        }
      }

      for(i=0;i<4;i++){ //verifica se o mesmo professor nao esta ministrando duas aula no mesmo horario
        for(j=i+1;j<5;j++){
          for(k=0;k<16;k++){
            if(this.melhorIndividuo[0].turma[i].week[k].prof===this.melhorIndividuo[0].turma[j].week[k].prof){
              //eslint-disable-next-line
              console.log("turma " + i + " turma " + j + " possuem mesmo professor na posição: "+ (k+1))

            }
          }
        }
      }

      }
    },

    generateSemana:function(){
    
      var k,i, prof, disc, score;
      var semana, turma = []
      for(k=0;k<=4;k++){
        semana = []
        for(i=1;i<=16;i++){
            disc = Math.floor(Math.random() * 20);           
            prof = Math.floor(Math.random() * 10); 
            semana.push({prof,disc})
          }
        turma.push({week:semana}) 
       }   
      score = this.fitness(turma);
      turma.push({score:score})
      return turma;
    },

    fitness: function(turmas){
      var i,j,k,score = 0;

      for(i=0;i<4;i++){ //verifica se o mesmo professor nao esta ministrando duas aula no mesmo horario
        for(j=i+1;j<5;j++){
          for(k=0;k<16;k++){
            if(turmas[i].week[k].prof===turmas[j].week[k].prof){
              score = score + 5;
            }
          }
        }
      }
      var ch= 0;

      //verifica se a carga horario semanal do professor nao ultrapassa 20h ou é menor que 8h
      for(k=0;k<10;k++){//percorre lista de professores
        ch = 0;
        for(i=0;i<5;i++){//percorre turmas
          for(j=0;j<16;j++){//percorre semana/dias
            if(turmas[i].week[j].prof===k){
              ch = ch + 2;
            }
          }
        }
        if(ch > 20 || ch < 8){ // caso ch > 20h ou ch < 8h score + 15
          score = score + 15;
        }
      }

      return score;
      
    },
    
    AlgoritmoGenético(){
        
      var pai1, pai2,  cont = 1;
      var newPop = [],aux = [];
      var i;
      for(i=0;i<100;i++){
        while(cont <= 50){
          aux = []
          pai1 = this.TournamentSelection();
          pai2 = this.TournamentSelection();
          aux.push({turma:this.CrossOver(this.populacao[pai1],this.populacao[pai2])})
          newPop.push({turma:aux[0].turma[0]})
          newPop.push({turma:aux[0].turma[1]})
          cont++;
        }
        this.populacao = []
        this.populacao = newPop
        newPop = []
        cont = 0
        }

        this.ultimageracao = this.populacao;
      //encontra o melhor valor de fitness 
       var melhor = [];
      for(i=0;i<100;++i){  
          melhor.push(this.populacao[i].turma[5].score)
      }
      var small = melhor[0]
      for(i=1;i<100;i++){//encontra menor valor fitness
        if (melhor[i] < small){
            small = melhor[i]}}

        //eslint-disable-next-line
      console.log("melhor individuo score: " + small)
       for(i=0;i<100;i++){
         if(this.populacao[i].turma[5].score === small){
              this.melhorIndividuo.push(this.populacao[i])
              i=100;
              }
       }
       this.cond = 3;
       this.CHprofessor();
       this.cond=1;
        

        for(i=0;i<10;i++){//imprime ch dos professores
        //eslint-disable-next-line
        console.log("ch professor " + i + " : " + this.professores[i].ch)}
    },

    CrossOver: function(pai1,pai2){
      //efetua o cruzamento entre duas turmas
      var semana1 = [], semana2 = []
      var turma1 = [], turma2 = []
      var valorCorte = Math.floor(Math.random() * 3) + 1
      var i,k;
      var score;
      
      for(k=0;k<5;k++){
          semana1 = []
          semana2 = []
          for(i=0;i<16;i++){
              if(i<valorCorte*4){
                semana1.push(pai2.turma[k].week[i])
                semana2.push(pai1.turma[k].week[i])
                }
              else{
                semana1.push(pai1.turma[k].week[i])
                semana2.push(pai2.turma[k].week[i])
                } 
           }
          
          turma1.push({week:semana1})
          turma2.push({week:semana2})

      }
     
      
      
      //mutacao
       //o cromossomo tem 10% de chance de ser mutado

        var auxiliar
        var chance = Math.floor(Math.random() * 10)+1;
        var randomTurma, randomWeek1, randomWeek2

        if(chance === 1){
          //eslint-disable-next-line
        //console.log('MUTOU!!!')
        randomTurma = Math.floor(Math.random() * 4);
        randomWeek1 = Math.floor(Math.random() * 15);
        randomWeek2 = Math.floor(Math.random() * 15);
        auxiliar = turma1[randomTurma].week[randomWeek1]
        turma1[randomTurma].week[randomWeek1]=turma1[randomTurma].week[randomWeek2];
        turma1[randomTurma].week[randomWeek2]= auxiliar}

        if(chance === 7){
          //eslint-disable-next-line
        //console.log('MUTOU!!!')
        randomTurma = Math.floor(Math.random() * 4);
        randomWeek1 = Math.floor(Math.random() * 15);
        randomWeek2 = Math.floor(Math.random() * 15);
        auxiliar = turma2[randomTurma].week[randomWeek1]
        turma2[randomTurma].week[randomWeek1]=turma2[randomTurma].week[randomWeek2];
        turma2[randomTurma].week[randomWeek2]= auxiliar}

      //fim mutacao        

      score = this.fitness(turma1);
      turma1.push({score:score})

      score = this.fitness(turma2);
      turma2.push({score:score})

      return [turma1,turma2]
    },

    TournamentSelection: function(){ 
      var i,melhor = [], vcandidato = [];
      var menor;
      //Utiliza tournament selection para encontrar primeiro pai
      vcandidato.push(Math.floor(Math.random() * 99) + 1,
                      Math.floor(Math.random() * 99) + 1,
                       Math.floor(Math.random() * 99) + 1)

      for(i=0;i<3;++i){  
          melhor.push(this.populacao[vcandidato[i]].turma[5].score)
      }

      menor = Math.min(melhor[0],melhor[1],melhor[2])

      for(i=0;i<3;++i){  
          if( menor === this.populacao[vcandidato[i]].turma[5].score){
            return vcandidato[i];
          }
      }
    }

  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: auto;
  margin-bottom: 60px;
}
button{
    background-color: #4CAF50;
    border: none;
    color: white;
    padding: 12px 20px;
    text-decoration: none;
    margin: 4px 2px;
    cursor: pointer;
  }
/* Pattern styles */
.container {
  display: table;
  width: 100%;
}

.left-half {
  position: absolute;
  left: 0px;
  width: 50%;
}

.right-half {
  position: absolute;
  right: 0px;
  width: 50%;
}
</style>
