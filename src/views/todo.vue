<template>

<div class="home">

  <h1>Todo Page</h1>
    <v-text-field
   
    v-model.trim="newTasktitle"
    id="newTasktitle"
    class="pa-2"
            outlined
            @click:append="searchString"
            @keyup.enter="searchString"
            label="add Task"
            append-icon="mdi-plus"
            hide-details
            clearable
         
        
          ></v-text-field>

    <v-list
      flat
      class="pt-0"
    >
    <div 
      v-for="task in tasks" :key="task.id"
      >

        <v-list-item @click="doneTask(task.id)" :class="{'blue lighten-5' : task.done}" >
          <template>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
               
              <v-list-item-title  
              :class="{'text-decoration-line-through' : task.done} " >
               {{task.input}} 
             
             
            
             </v-list-item-title>
              
            </v-list-item-content>
               <v-list-item-action>
          <v-btn @click.stop="deleteTask(task.id)">
            <v-icon color="primary">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>
      
          </template>
        
        </v-list-item>
        <v-divider ></v-divider>
        <div v-html="becomeText">

</div>
        </div>
       
    </v-list>
   
    </div>

</template>

<script>
 // import HelloWorld from '../components/HelloWorld'

  export default {
    name: 'Home',
    
    data(){

return {

  newTasktitle :'',
  single : '',

  tasks: [

 /*{   id : 1,
    title : 'Wake Up',

    done : false
    },

    {   id : 2,
    title : 'INpout',
    done : false
    },
      {   id : 3,
    title : 'Get',
    done : false
      }
      */

  ],
  



arr : [],
  returnArr : [],

  change : true,

   becomeText : '',


  
   str : ''
}


    },
  methods : {

  /*  addTask(){

      let newTask = {

id : Date.now(),
title : this.newTasktitle,
done: false
      }

      this.tasks.push(newTask)
      this.newTasktitle = ''

    },
*/



 searchString()  {



   let newInput = {  

      id :  Date.now(),
     input :  this.newTasktitle,
 
  done  : false


  
  }

  /*  if(this.newTasktitle === ""){
    this.error.push('text required');

   }
*/
//console.warn('Ok');





var text ='La donzelletta vien dalla campagna\
in sul calar del sole,\
col suo fascio dell\'erba; e reca in mano\
un mazzolin di rose e viole,\
onde, siccome suole, ornare ella si appresta\
dimani, al dí di festa, il petto e il crine.\
incontro là dove si perde il giorno;\
e novellando vien del suo buon tempo,\
quando ai dí della festa ella si ornava,\
ed ancor sana e snella\
solea danzar la sera intra di quei\
ch\'ebbe compagni nell\'età piú bella.\
Già tutta l\'aria imbruna,\
torna azzurro il sereno, e tornan l\'ombre\
giú da\' colli e da\' tetti,\
al biancheggiar della recente luna.\
Or la squilla dà segno\
della festa che viene;\
ed a quel suon diresti\
che il cor si riconforta.\
I fanciulli gridando\
su la piazzuola in frotta,\
e qua e là saltando,\
fanno un lieto romore;\
e intanto riede alla sua parca mensa,\
fischiando, il zappatore,\
e seco pensa al dí del suo riposo.\
\
Poi quando intorno è spenta ogni altra face,\
e tutto l\'altro tace,\
odi il martel picchiare, odi la sega\
del legnaiuol, che veglia\
nella chiusa bottega alla lucerna,\
e s\'affretta, e s\'adopra\
di fornir l\'opra anzi al chiarir dell\'alba.\
\
Questo di sette è il più gradito giorno,\
pien di speme e di gioia:\
diman tristezza e noia\
recheran l\'ore, ed al travaglio usato\
ciascuno in suo pensier farà ritorno.\
\
Garzoncello scherzoso,\
cotesta età fiorita\
è come un giorno d\'allegrezza pieno,\
giorno chiaro, sereno,\
che precorre alla festa di tua vita.\
Godi, fanciullo mio; stato soave,\
stagion lieta è cotesta.\
Altro dirti non vo\'; ma la tua festa\
ch\'anco tardi a venir non ti sia grave.'






var Context=text.split(' ');

if(this.newTasktitle == ''){

  return false
}

if(text.includes(this.newTasktitle)){

  var stringValue='';
console.log(Context);


this.tasks.push(newInput);


for(var i=0; i<Context.length; i++){


 this.arr.push(Context[i] + "\n");
 
 var fullText= this.arr.toString();




var takeThis = this.newTasktitle;





this.becomeText=
fullText.replace(takeThis,function (x) {

         
return '<b style="color:green">'+x+'</b>';
  });







}







}else{

  alert('Not found ');
}


 

  },

  


 FontColor(color,textHolder){
	textHolder.style.color = color;
},



 
  
    doneTask(id){
      




  let task =this.tasks.filter(task => task.id === id)[0];



      task.done = !task.done
  
    },


  
    

    deleteTask (id){

      this.tasks = this.tasks.filter(task => task.id  !== id)
    },



  }

 
  }

    

   
  
</script>
<style scoped src="../assets/style.css">

</style>