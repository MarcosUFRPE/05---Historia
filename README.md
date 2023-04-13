# 05---Historia
//PARTE DAS CLASSES ,CONSTRUTORES,METODOS.
-----------------------
classe =Escolha.java
----------------------
public class Escolha {
    String texto;
    Capitulo proximo;

   Escolha(String texto,Capitulo proximo){

       this.texto=texto;
       this.proximo=proximo;
   }
}
-------------------------------------
classe Caracteristicapersonagem.java
-------------------------------------
public class Caracteristicapersonagem {
    String nome;
    float altura;
    int idade;
    int energia; 

     void qtenergia(int novaenergia){
      this.energia=this.energia + novaenergia;
       if(novaenergia>0){
         System.out.println(",sendo assim "+ this.nome + "ganhou " + novaenergia +
         " pontos de energia" );

       }else if(novaenergia<0){

          System.out.println(",sendo assim " + this.nome + " perde " + novaenergia +
          " de energia");

       }



       if(this.energia>300){
          this.energia=300;
        }else if(this.energia<=0){
           this.energia=0;


           
           System.out.println( "como " + this.nome  +  " perdeu toda sua energia ,ele morreu" );
           System.out.println(".............................................................");
      }

     }
}

-----------------------------------------------------------
classe=Capitulo.java
-----------------------------------------------------------
import java.util.ArrayList;
import java.util.Scanner;

public class Capitulo {
  
  Caracteristicapersonagem personagem;
  int novaenergia;
  String  nome;
  String texto;
  ArrayList<Escolha> escolhas;
  Scanner his;
  



        Capitulo( Caracteristicapersonagem personagem,
                   int novaenergia,
                   String  nome,
                  String texto,
                  
                  Scanner his
                   )
           {

            this.personagem=personagem;
            this.novaenergia=novaenergia;
            this.nome=nome;            
            this.texto=texto;                   
            this.his=his;
            this.escolhas=new ArrayList<Escolha>();
        }


            
            /**
             * 
             */
             void mostra(){
              
              System.out.println(this.nome);
              System.out.println("________________________________");
              System.out.println(this.texto); 
              this.personagem.qtenergia(this.novaenergia);
              System.out.println("_________________________________");
           if (this.escolhas.size()>0){
               for(Escolha escolha : escolhas){

                   System.out.println(escolha.texto);
                  }

                
              System.out.println("________________________________");
          

               int nescolha=escolher();
               this.escolhas.get(nescolha).proximo.mostra();

           }              
            }
 
            int escolher(){

              int nescolha=-2;

              if (escolhas!=null){
               
                
                while(nescolha==-2){
                String resp= his.nextLine();
                for (int n = 0; n < escolhas.size(); n++) {
                 
                  if ( resp.equals(escolhas.get(n).texto)){ 
                     nescolha=n;
                }
              }

              }
           
              }
             return nescolha;
            }

           }

 ---------------------------------------------------------       
PARTE DA HISTORIA INTERATIVA
----------------------------------------------------------
public static void main(String[] args) {
      
      
           
        
      Caracteristicapersonagem martin =new Caracteristicapersonagem();
      martin.nome="martin";
      martin.energia=100;
      martin.qtenergia(0);
   Caracteristicapersonagem assassino =new Caracteristicapersonagem();
     assassino.nome="assassino"; 
     assassino.energia=100;
     assassino.qtenergia(0);
   Caracteristicapersonagem joana =new Caracteristicapersonagem();
     joana.nome="joana";   
     joana.energia=100;
     joana.qtenergia(0);  
    Caracteristicapersonagem espiritochefe=new Caracteristicapersonagem();
      espiritochefe.nome="joao";
      espiritochefe.altura=3.00f;
      espiritochefe.idade=500;
      espiritochefe.energia=300;
      espiritochefe.qtenergia(0);
   








      


         
          
         Scanner his=new Scanner(System.in);
         
         
         Capitulo capitulo1=new Capitulo( martin,
            0,
            "A  TRILHA PELA FLORESTA", 
           " Um certo dia três amigos,"+martin.nome+","+assassino.nome+" e "+joana.nome+ ",resoveram fazer uma trilha pela floresta"
           +" "+",chegando lá  eles avistaram uma  casa abandonada. " +
           "O que eles tem que fazer?",
                
          his
           
         );

         
            
         
         
         
          Capitulo raiz=capitulo1;
         
      
      
            

            Capitulo capitulo3=new Capitulo( martin,
               0,
               "A CHEGADA A  CASA ABANDONADA", 
               " Chegando na casa abandonada ,eles entram e encontram um livro chamado ,os 7 espirito amaldiçoado . " +
               " o que eles tem que fazer? ",
                 his
             
              );

              capitulo1.escolhas.add( new Escolha("ir até a casa",capitulo3));
            

            
         
            


           
            
            Capitulo capitulo4=new Capitulo(assassino,
               -10,
               "O ENCONTRO COM O ESPIRITO ", 
            "E assim que eles acabaram de ler o livro ,sete espito amaldiçoado despertam para atormentar a vida daqueles " +
            "que acordaram eles de seu sono profundo e entre esses sete espito está o " + espiritochefe.nome +
            " um espirito de "+" "+ espiritochefe.altura + "m de altura e " + espiritochefe.idade + " anos  de idade " +
            "e que quando era um homem foi um psicopata que matou milhares de pessoas "+
            "e que  quando a policia pegou ele  torturou e matou ele nessa casa abandonada   e até " +
            "hoje seu espito vive nessa casa,sendo o lider dos outros seis espirito  ." + 

            "Agora a missão dos três amigos é encontrar uma forma de fazer com que os 7 espiro voltem "+
            " para o seu sono profundo,caso não  "+
            " os espirito vão pegar  atormenta e tortura eles ate morre. "+
            "sedo  que as portas da casa abandonada se fecharam quando os espiritos depestaram  "+  
            "assim os tres amigos nao tem como simplemente sair da casa . "  +
            "como eles nao conseguia sair da casa resolveram caçar alguma soluação dentro da casa " +
            " em busca de alguma solução eles acabam dando de cara com um dos espitos que acaba atacando eles " +
            "e que acaba acertado ,"+assassino.nome+  " , com uma paulada  fazendo com quer " +assassino.nome  +
            " perca  energia "
            
           ,           
            his
             
              );
            
            capitulo3.escolhas.add( new Escolha("eles pegam o livro e ler  ",capitulo4));
           

            Capitulo capitulo5=new Capitulo(martin,
               0,
               "O LIVRAMENTO",
               "E deixando o livro quieto eles se livra do tormento dos 7 espiritos amaldiçoados." ,
                              
               his
               );
            capitulo3.escolhas.add( new Escolha("deixam o livro queto  ",capitulo5));
         
           
           
         

             Capitulo capitulo2=new Capitulo(martin,
               0,
               "DIA NORMAL",
               "  E assim foi mais um dia normal na vida deles!",
               
               his
               
                );
             
                


         
            
             capitulo1.escolhas.add( new Escolha("passar direto ",capitulo2));
                
             raiz.mostra(); 
       his.close();
          
      }
    
   }


   



