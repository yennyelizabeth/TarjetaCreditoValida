==========================================
TARJETA DE CREDITO VALIDA
==========================================

PSEUDOCODIGO
==========================================
1.- Solicitar Número de Tarjeta de crédito (tarjet)
2.- Leer Número de Tarjeta de Credito (tarjet)
3.- Validar tarjet (Si/No)
4.- Si tarjet no es válida ( 'vacío o letras)
    4.1.- Leer ' Número no válido'
    4.2.- Regresar a paso nro 1
5.- Si tarjet si es válida ( no es 'vacío' y 'no es letra')
6.- Hacer la validación tomando en cuenta las posiciones impares y pares



CODIGO JAVASCRIPT APP.JS
=========================================

// declarando e inicializando variables

var arrayInitial=[]; // array que contendra el numero de tarjeta por cada caracter
var arrayResult=[];  // array que contendrá los nuevos valores según sea posición impar o par
var tempNumber=0;    // variable numérica temporal para la operación de posiciones pares
var tempString='';   // variable string temporal para la operación de posiciones pares
var acumulate=0;     // acumula los valores de valores de arrayResult para la validación final
var count= 0;
var validate=false ; // variable que controlara la validación de ingreso de número de tarjeta

// Realizando el Ingreso y controlando el Ingreso de Número de Tarjeta
do {

     var tarjet= prompt('Ingrese Número de Tarjeta: ') ; // se solicita nro de tarjeta de crédito
     var n= tarjet.length;// captura el tamaño de longitud de la variable tarjet
     //sentence = prompt('ingrese frase: ');

     if (tarjet.length ===0){
        alert('No ingreso Número de Tarjeta:') ;
        var validate=false
     }else{

         count=0;

         for (var a=0; a< tarjet.length ; a++){

           if(tarjet.charCodeAt(a)>=48 & tarjet.charCodeAt(a)<=57 ) {
              validate=true;
              count= count+1;
           }
         }

         if( count === tarjet.length){
           validate=true;
           alert('Ingreso Correcto : '+ tarjet);
         } else{
           validate= false;
           alert('Ingreso Incorrecto: '+tarjet)
         }
     }
} while (validate === false);

if (validate=== true){
   isValidCard (tarjet);
}


// Función Validación de Tarjeta
function isValidCard ( tarjet){

// utilizar un for para armar un arrayInitial invertida
for (var i=0 ; i<n ; i++){
    arrayInitial[i+1]= parseInt(tarjet.substr(i,1));
}

// utilizar un for para armar un arrayResult a traves del arrayInitial
for ( var j=1; j <= tarjet.length; j++){

    // utilizo un if para identificar posicion par o impar
    if ( j %2 !== 0){
       arrayResult[j]= arrayInitial[j] ; //valores de posiciones impares
       acumulate +=  arrayResult[j]; // acumula valor posicion impar
    } else {
      tempNumber = arrayInitial[j]*2

    // utilizo if para controlar la divisibilidad entre 10
      if ( tempNumber >=10){
         tempString = tempNumber.toString();
         arrayResult[j] = parseInt(tempString.substr(0,1))+parseInt(tempString.substr(1,1)); //valores posiciones pares segun operacion >=10
         acumulate +=  arrayResult[j]; // acumula valor posicion par
      } else{
        arrayResult[j]= arrayInitial[j] // valores de posiciones pares <10
        acumulate += arrayResult[j];  // acumula valor posicion par
      }
    }
}

  if ( acumulate%10 ===0){
    alert('Tarjeta de Credito SI Válida');

  } else {
    alert('Tarjeta de Credito NO Válida');
    alert( 'Valor Acumulado:   '+acumulate);
  }
}
