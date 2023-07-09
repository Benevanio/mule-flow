# Mule-Flow
Está api faz o uso dos seguintes componentes:

# Set Payload:
 Este componente é usado para definir o payload da mensagem que será passado para o próximo componente. Ele pode ser usado para definir o payload como uma string, objeto ou qualquer outro tipo de dados.

# Transform Message: 
Este componente é usado para transformar a mensagem de entrada em um formato diferente. Ele pode ser usado para converter a mensagem de um formato para outro, como XML para JSON.
 A linguagem usada na criação desta API foi: # Dataweave:
 Este componente é usado para transformar dados de um formato para outro. Ele é usado principalmente para transformar dados em um formato que possa ser consumido por outros sistemas. O Dataweave suporta vários tipos de dados, incluindo XML, JSON e CSV.
# Aqui esta um exemplo do MAP.
````
output application/json
var a =[
	{
		name: "bene",
		id: 82,
		org: ["Google","Sysmap"]
	},
	{
		name: "berlan",
		id: 52,
		org: ["Google","TESLA"]
	},
		{
		name: "beniel",
		id: 52,
		org: ["IBM","Banco do Brasil"]
	},
		{
		name: "benevan",
		id: 22,
		org: ["Google","Banco do Brasil"]
	},
]
---
/*
 *a map(value, index) ->{
	(index): value
}
* a map ((item, index) ->{
	"userName": upper(item.name),
	"Company": item.org,
	//"uniqueID": item.name ++ "-" ++  item.id ++ "-" ++ item.org,
	"Index da nossa aplicação": index
}) 
 */

//
a map ((bene, number) ->{
	"CandidateName": upper(bene.name),
	"Company":bene.org map{
		"Company-Name": $ ++ bene.name
	},
	"Index da nossa aplicacação" : number
})

````
# explicacao 

No inicio da primeira linha temos a definiçao do tipo de saida de dados em nosso sistema(Json), Na segunda parte temos a variavel "a" que é definida como uma matriz , logo em seguida nos temos o map.
O "map" é uma função em Dataweave que é usada para iterar sobre uma matriz e executar uma operação em cada elemento da matriz. A função "map" retorna uma nova matriz com os resultados da operação aplicada a cada elemento da matriz original.  

## Demonstração

demo no AnyPoint Studio

![Demo-AnyPoint Studio](https://github.com/benetesla/mule-flow/assets/78994881/14bd46a8-d544-4a53-b3a7-5432d01cab4b)


![Demo-Postman](https://github.com/benetesla/mule-flow/assets/78994881/a7358909-7fc0-49bb-8463-2e7f968a5ac3)

## Referência

 - [mule-demo](https://github.com/mulesoft/mule-api)
 
