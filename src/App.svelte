<script>
	let total = 0;
	let console = "";
	let state = null;
	const resolveState = () =>{
		switch(state){
			case "+":
				total += parseFloat(console);
				console ="0";
				break;
			case "-":
				total -= parseFloat(console);
				console = "0";
				break;
			case "*":
				total *= parseFloat(console);
				console = "0";
				break;
			case "/":
				total /= parseFloat(console);
				console = "0";
				break;
			default:
				total = parseFloat(console);
				console = "0";
				break;
		}
	};
	const setOperation = (operation) =>{
		resolveState();
		state = operation;
	};
	const setValue = (value) =>{
		if(console.toString() == "0" || state == "equal"){
			console = "";
		}
	
		if(state == "equal"){
			state = null;
		}
		
		if(value == "C"){
			total = 0;
			state = null;
			console = "";
			return;
		}
		console = console + value;
	};

	const equal=()=>{
		resolveState();
		console = total;
		state = "equal";
	};

</script>

<main>
	<h1>Calculator</h1>
	<div class="calculator">
		<div class= "input">
			<input type="text" bind:value={console} readonly="true"/>
		</div>
		<div class="buttons">
			<button on:click={()=>{setValue('C');}} class="button1">C</button>
			<button on:click={()=>{setOperation('+');}}>+</button>
			<br>
			<button on:click={()=>{setValue('7');}}>7</button>
			<button on:click={()=>{setValue('8');}}>8</button>
			<button on:click={()=>{setValue('9');}}>9</button>
			<button on:click={()=>{setOperation('-');}}>-</button>
			<br>
			<button on:click={()=>{setValue('4');}}>4</button>
			<button on:click={()=>{setValue('5');}}>5</button>
			<button on:click={()=>{setValue('6');}}>6</button>
			<button on:click={()=>{setOperation('*');}}>×</button>
			<br>
			<button on:click={()=>{setValue('1');}}>1</button>
			<button on:click={()=>{setValue('2');}}>2</button>
			<button on:click={()=>{setValue('3');}}>3</button>
			<button on:click={()=>{setOperation('/');}}>÷</button>
			<br>
			<button on:click={()=>{setValue('.');}}>.</button>
			<button on:click={()=>{setValue('0');}}>0</button>
			<button on:click={equal} class="button2">=</button>
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}


	.calculator {
		margin: auto;
		border-color: black;
		border-style: inset;
		height: fit-content;
		width: fit-content;
		padding: 10px;
		padding-top: 20px;

	}
	.calculator input{
		text-align: right;
		width: 250px;
		height: 40px;
	}
	.calculator .buttons .button1{
		padding: 15px;
		width: 160px;
	}
	.calculator .buttons .button2{
		padding: 15px;
		width: 106px;
	}
	.calculator .buttons button{
		padding: 15px;
		width: 50px;
	}


	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>