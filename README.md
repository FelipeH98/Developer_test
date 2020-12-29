# Developer Test for LocalShop
### 1- Describe the process you have for a programming task(from requirements to delivery).
```
My process while programming: 

- Initially I analyze the task that I'm working on and try to define input and output data for it.

- If it's a complex task, I usually write steps that I need to solve the task before I code it,
  that's help me a lot to understand the whole problem and find the best solution.
  
- When I'm coding I leave a comment next to the most important lines or functions explaining what it does.

- After programming, I test the solution with static parameters or any other method according to the type of task.
  All that include thinking about possible bugs that I can solve to optimize the task.
```
### 2- Databases are the most common way to storage data in complex aplications, these days are different types of them separated in relational databases(SQL) and non-relational databases explain the good vs bad about them and in wich case you will use one or another.
```
SQL: Tables have direct relations using PK and FK. Allow an easy and fast way to relate data but a slower way to read it.
SQL is better for write data but not for read it.

SQL can be used business purpose when you need to analize information and do Business Inteligence, 
also it can be used for companies that need to keep a consistent data structure.

NO-SQL: Doesn't have direct relations but allow something similar imitating direct relations. 
Developer has the responsability when he need to join information. NO-SQL is god at reading data but not for writing.

NO-SQL can be used for Web Development just like SQL, also it can be used for Mobile Development and 
Big Data due to the large amount of data that need to be managed.
```
### 3- Grab any invoice and create a database to store the data on it, create the entity diagram and database dictionary too.
#### Invoice image (Google)
![Diagrama](img/factura.png)
#### Diagram
![Diagrama](img/diagrama.PNG)
### Database dictionary
![Diagrama](img/tabla-ciudad.PNG)
![Diagrama](img/tabla-comuna.PNG)
![Diagrama](img/tabla-direccion.PNG)
![Diagrama](img/tabla-cliente.PNG)
![Diagrama](img/tabla-factura.PNG)
![Diagrama](img/tabla-pago.PNG)
![Diagrama](img/tabla-detalle-factura.PNG)
![Diagrama](img/tabla-item.PNG)


### 4- Someone ask you to create a webapp to chat with clients, this should support Whatsapp and Facebook Messenger, Which architecture and technologies will you use?(please add a diagraman in your answer)
```
```
### 5- What is your process to test and find bugs in an application?
```
```
### 6- What do you know about Cloud Computing?
```
```
### 7- What do you know about Agile software development process?
```
```
### 8- remember question number 3?. Create a query to obtain all data from the tables you create to store invoice data
```
```
### 9- Create a JSON with your personal data, include at least 1 object and 1 array
```
```
### 10- Finding errors is a good skill to have, please review the next code and tell us what is the problem, why the message is trigered before is intended? do the nessesary changes in the code to fix it.
#### I run this with NodeJS
```javascript 
const moment = require("moment-timezone");
const { db } = require("../../../firebase"); //Comente esta linea para la ejecución con Node.

const getOpenedBusiness = async(dialogflowInfo) => {
    let intentResponse = {};
    let closedBussiness = false;
    let merge_behavior;
    let textToRespond = "";
    const chileTime = moment().tz('America/Santiago');
    const openAt = 10;
    const monthDay = chileTime.format('MM-DD');
    //Cambio de formato de 'hh:mm'(12hrs) a 'HH:mm'(24hrs) debido a que linea 44 (2do IF) compara currentHourMinute con hora en formato 24hrs. 
    const currentHourMinute = chileTime.format('HH:mm');
    const beforeOpenAt = chileTime.hour() < openAt; // Es true si hora actual es < hora de apertura.
    intentResponse.merge_behavior = "APPEND";

    // Mostrar const usadas para conocer formato.
    // console.log(`
    // - Chile Time: '${chileTime}'
    // - monthDay: '${monthDay}' 
    // - currentHourMinute: '${currentHourMinute}'
    // - beforeOpenAt: '${beforeOpenAt}'
    // - Chile Time Hour: '${chileTime.hour()}'
    // `)

    //Se muestra en los dias comparados con dia y mes presentes '12-14,12-25,12-31,01-01' desde las 19 hrs inclusive.
    if ((monthDay === "12-24" || monthDay === "12-28" || monthDay === "12-31" || monthDay === "01-01") && (chileTime.hour() >= 19)) {
        textToRespond = `¡Hola! 
        👋🏼\n\n\t\t A nombre de todo el Equipo de Localshop y en\n representación de todos los locales y shoppers que son\n parte de esta hermosa red,
        te damos las gracias por\n todo el apoyo que has entregado a la vida de barrio.
        \n\n\t\t En estas fiestas 
        estaremos apoyándote en los\n siguientes horarios:
        \n\n- 24 Dic: 10:00 a 19:00 hrs\n- 
        25 Dic: Cerrado\n- 
        31 Dic: 10:00 a 19:00 hrs\n - 
        1 Enero : Cerrado \n\n 
        ¡Te deseamos felices fiestas y que \n tengas un excelente 2021!`;
        intentResponse.merge_behavior = "REPLACE";
        closedBussiness = true;
        // console.log(textToRespond);
    }

    // Se muestra antes de las 10 de la mañana o despues de las 20:30 inclusive, con condicional si beforeOpenAt es true OR hora actual es >= a 20:30.
    if (beforeOpenAt || currentHourMinute >= "2030") {
        textToRespond = `¡Hola! 👋🏼\n\nGracias por comunicarte con Localshop.
        Tus tiendas de barrio volverán a recibir pedidos desde las 10:00 AM!
        \nPuedes dejar tu pedido escrito acá o elige directamente en www.localshop.cl y te escribiremos en la apertura para procesarlo.\n\n¡Gracias por cuidar la vida de barrio! 🏡`;
        intentResponse.merge_behavior = "REPLACE";
        closedBussiness = true;
        // console.log(textToRespond);
    }

    intentResponse.textToRespond = textToRespond;
    intentResponse.session_info = {
        parameters: {
            closedBussiness //Asignación optimizada de closedBussiness: closedBussiness 
        }
    };
    // console.log(intentResponse);
    return intentResponse // returning intentResponse { merge_behavior: 'APPEND', textToRespond: '',session_info: { parameters: { closedBussiness: false } } } si no entra a ningún if.
}

// getOpenedBusiness();

module.exports = getOpenedBusiness;
```

### Challenge 1: reactJS
```
- create a simple reactJs app for adding products to a store
- at least create and use 3 components
- you can use mock data (JSON)
- should be very simple but think about the UI/UX
- create a github repo, upload your code and send us the link 
- you are free to use any additional framework, library you want to
```

#### Solution's repository
<https://github.com/FelipeH98>

### Challenge 2: Chatbot
```
- create a simple chatbot that answer frequent questions about become a Shopper, you can look for information in https://site.localshop.cl/TyC you can use any avaiable free tier tools from AWS, IBM, Microsoft or Google
- let us know if you complete this challenge. We will contact you so we can test it
```
#### Solution's repository
<https://github.com/FelipeH98>
