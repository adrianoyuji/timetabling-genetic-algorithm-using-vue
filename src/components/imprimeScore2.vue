<template>
    <div>
       <table id="firstTable">
        <thead>
          <tr>
            <th>Indivíduo</th>
            <th>Score</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="row in rows" v-bind:key=row.id>
            <td>{{row.index}}</td>
            <td>{{row.score}}</td>
          </tr>
        </tbody>
    </table>
    </div>
</template>

<script>
export default {
    props:{
        primeira:Array,
        ultima:Array
    },
    data() {
        return {
            rows:[],
        }
    },
    
    methods: {
        imprimeDados(primeira){
            
            var i;
            primeira.sort(function(a,b){
              if(a.turma[5].score > b.turma[5].score){
                return 1;
              }
              if(a.turma[5].score < b.turma[5].score){
                return -1;
              } return 0;
            })

            for(i=0;i<100;i++){
            this.rows.push({index:i+1, score:primeira[i].turma[5].score})
            }

        }
    },
    
    watch: {
      
    ultima: {
        handler(ultima) {
        this.imprimeDados(ultima)
        },
        immediate: true
    }
  }


}
</script>

<style scoped>
table {
  font-family: 'Open Sans', sans-serif;
  width: 500px;
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