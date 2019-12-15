<template>
    <div>
      <table id="firstTable">
        <thead>
          <tr>
            <th>Horário</th>
            <th>Segunda</th>
            <th>Terça</th>
            <th>Quarta</th>
            <th>Quinta</th>
            <th>Sexta</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="row in rows" v-bind:key=row.id>
            <td>{{row.horario}}</td>
            <td>{{row.seg}}</td>
            <td>{{row.ter}}</td>
            <td>{{row.qua}}</td>
            <td>{{row.qui}}</td>
            <td>{{row.sex}}</td>
          </tr>
        </tbody>
    </table>

</div>
</template>

<script>

export default {

    props:{
        mat:Array
    },

    data(){
        return {
        semana:[],
        rows:[{id:1,horario:'7:20', seg:'',ter:'',qua:'',qui:'',sex:' - '},
            {id:2, horario: '9:15', seg:'',ter:'',qua:'',qui:'',sex:' - '},
            {id:3, horario: '13:20', seg:'',ter:'',qua:'',qui:'',sex:' - '},
            {id:4, horario: '15:20', seg:'',ter:'',qua:'',qui:'',sex:' - '}],

            professores:[{nome:'Felipe Carbone', id:1},
                       {nome:'Valguima Odakura',id:2},
                       {nome:'Marcos Furlan', id:3},
                       {nome:'Silvana Melo', id:4},
                       {nome:'Marcos Paulo Moro', id:5},
                       {nome:'Rodrigo Sacchi', id:6},
                       {nome:'Willian Paraguassu', id:7},
                       {nome:'Carlos Zampieri', id:8},
                       {nome:'Alfred Forster', id:9},
                       {nome:'Alexandre Szabo', id:10},
                       {nome:'Murilo Taparo', id:11}],

      cursos:[{nome:'INTELIGÊNCIA ARTIFICIAL', id:1, ch:72},
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
             {nome:'EMPREENDEDORISMO',id:20, ch:72},
             {nome:'OPTATIVA I',id:21, ch:72}],

          
        
    }},

    methods: {
        trataDados(value){
            var i=0,j=4;
            while (i<17){
                this.semana.push(value.slice(i,j))
                i=i+4;
                j=j+4;
                }

        for(i=0;i<4;i++){    
            this.rows[i].seg = ("Professor: " + this.professores[this.semana[0][i].prof].nome+
             " Disciplina: " + this.cursos[this.semana[0][i].disc].nome)
            this.rows[i].ter = ("Professor: " + this.professores[this.semana[1][i].prof].nome+
             " Disciplina: " + this.cursos[this.semana[1][i].disc].nome)
            this.rows[i].qua = ("Professor: " + this.professores[this.semana[2][i].prof].nome+
             " Disciplina: " + this.cursos[this.semana[2][i].disc].nome)
            this.rows[i].qui = ("Professor: " + this.professores[this.semana[3][i].prof].nome+
             " Disciplina: " + this.cursos[this.semana[3][i].disc].nome)
        }

        }
    },

    watch: {
      mat: {
        handler(mat) {
        this.trataDados(mat)
        },
        immediate: true
    }
  }
    
}
</script>

<style scoped>
table {
  font-family: 'Open Sans', sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin:auto;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: center;
  padding: 8px;
  border-right: 2px solid #7D82A8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #D4D8F9;
}
</style>