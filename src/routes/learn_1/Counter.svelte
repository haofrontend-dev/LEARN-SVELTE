<script>
	let count = 0;

	const increment = () => {
		count += 1;
	};

	//Để tính toán giá trị từ các phần khác của trạng thái và cập nhật chúng khi có sự thay đổi, giống với computed của vuejs
	$: double = count + 2;

	$: {
		console.log(`the count is ${count}`);
		console.log(`this will also be logged whenever count changes`);
	}

	$: if (count >= 10) {
		alert('count is dangerously high!');
		count = 0;
	}

	/**
	 * Update array object
	*/
	let numbers = [1, 2, 3, 4]
	$: sum = numbers.reduce((total, currentNumber) => total + currentNumber, 0);
	const addNumber = () => {
		numbers = [...numbers,numbers.length + 1 ]
	}
</script>

<div class="counter">
	<h1>Counter: {count}</h1>
	<h1>Double: {double}</h1>
	<button on:click={increment}> {count === 1 ? 'time' : 'times'}</button>
</div>

<div class="count-array">
	<p>{numbers.join(' + ')} = {sum}</p>

	<button on:click={addNumber}>
		Add a number
	</button>
</div>
<style>
	.counter {
		border-top: 1px solid rgba(0, 0, 0, 0.1);
		border-bottom: 1px solid rgba(0, 0, 0, 0.1);
		margin: 1rem 0;
		text-align: center;
	}
</style>
