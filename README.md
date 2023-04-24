day7 countries us dollar task
var request=new XMLHttpRequest();
request.open("GET","https://raw.githubusercontent.com/rvsp/restcountries-json-data/master/res-countries.json");
request.send();
request.onload=function(){
  
    var result=JSON.parse(request.response);
    //console.log(result);
    //print the all the countries which belongs to Asia region
     var res=result.filter((ele)=>ele.region==='Asia').map((ele)=>ele.name);
    //console.log(res);


//you have to extract the counties details whose population is less than 2lAKH
var res1=result.filter((ele)=>ele.population<200000).map((ele)=>ele.name);
 //console.log(res1);


 //Print the following details name, capital, flag using forEach function
 var arr_population=[]; 
 result.forEach(details => {
        //console.log("Name:"+details.name+", Capital:"+details.capital+", Flag:"+details.flag);
        arr_population.push(details.population);

    });


//Print the total population of countries using reduce function
 var res2=arr_population.reduce((acc,ele)=>acc+ele);
//console.log(res2);

//Print the country which uses US Dollars as currency.
var arr_countries=[]; 
result.forEach(details1 => {
    if(details1.currencies[0]['code']==='USD'){
        arr_countries.push(details1.name);
    }
});

//another way 
//console.log(arr_countries);
var res4=result.filter((ele)=>ele.currencies[0]['code']==='USD').map((ele)=>ele.name);
//console.log(res4);
}
