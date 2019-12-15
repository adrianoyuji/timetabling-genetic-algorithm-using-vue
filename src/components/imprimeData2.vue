<template>
    <div>
        <table id="firstTable">
        <thead>
          <tr>
            <th>Professor</th>
            <th>Carga Horária Semanal</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="row in rows" v-bind:key=row.id>
            <td>{{row.nome}}</td>
            <td>{{row.ch + " horas"}}</td>
          </tr>
        </tbody>
    </table>
    </div>
</template>


<script>
export default {
    props:{
        professores:Array
    },
    
    data() {
        return {
            rows:[],
        }
    },
    methods: {
        imprimeDados(profs){
            
            var i;
            for(i=0;i<10;i++){
            //eslint-disable-next-line
            console.log(profs[i].ch)
            this.rows.push({nome:profs[i].nome, ch:profs[i].ch})
            }

        }
    },

    watch: {
      professores: {
        handler(professores) {
        this.imprimeDados(professores)
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
  text-align: center;
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