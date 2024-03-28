<script>
	import { writable } from 'svelte/store';
	const date = new Date();
	const reg = /^([1-9]|[1-2][0-9]|3[0-1])$/;
	const months = ['jan', 'feb', 'mar', 'apr', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec'];
	let i = 1;
	let modal;
	let dayvar1 = [];
	let dayvar2 = [];
	let month = months[date.getMonth()];
	let daysinmonth = writable(31);
	let ppl = [];
	let nod = [];
	let lpd = [];
	let tp = writable([0]);
	let sp = writable(0);
	let sum = 0;
	let showw = [];
	for (let y = 0; y < 32; y++) {
		dayvar1.push(0);
		dayvar2.push(0);
		ppl.push(0);
		nod.push(0);
		lpd.push(0);
		$tp.push(0);
		showw.push(true);
	}
	function switchmonth(monthin) {
		switch (monthin) {
			case 'jan':
				$daysinmonth = 31;
				break;
			case 'feb':
				$daysinmonth = 28;
				break;
			case 'mar':
				$daysinmonth = 31;
				break;
			case 'apr':
				$daysinmonth = 30;
				break;
			case 'may':
				$daysinmonth = 31;
				break;
			case 'jun':
				$daysinmonth = 30;
				break;
			case 'jul':
				$daysinmonth = 31;
				break;
			case 'aug':
				$daysinmonth = 31;
				break;
			case 'sep':
				$daysinmonth = 30;
				break;
			case 'oct':
				$daysinmonth = 31;
				break;
			case 'nov':
				$daysinmonth = 30;
				break;
			case 'dec':
				$daysinmonth = 31;
				break;
		}
	}
	function calcall() {
		sum = 0;
		for (let ca = 0; ca < i; ca++) {
			calc(ca);
			update(ca);
		}
	}
	function calc(ii) {
		nod[ii] = dayvar2[ii] - dayvar1[ii] + 1;
		$tp[ii] = lpd[ii] * nod[ii] * ppl[ii];
	}
	function clearsp() {
		sp.set(0);
		location.reload();
	}
	function update(ii) {
		sum = sum + $tp[ii];
		sp.set(sum);
	}
	function check31(e) {
		if (dayvar2[e - 1] != daysinmonth && reg.test(dayvar2[e - 1])) {
			i++;
		} else {
			alert(
				'You cannot create a situation because you reached the end of the month or you have not entered a day.'
			); //asdfXXXV2020 1555@januaryshellxngxcbiag5+🐔SnSnSnKHBHecolombia🌖lingo🐛🐛🐛🐛🐛🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️i am loved
		}
	}
</script>

<div class="clearfix text-center">
	<div class="card bg-dark w-19 left mt-5 border border-2 rounded-4">
		<div class="card-header">Milk price calculator</div>
		<div class="card-body">
			<div class="float-start text-center">
				<div class="">
					<label for="val3">Month : </label>
					<select
						name="gg3"
						id="val3"
						class="btn py-1 fs bg-secondary text-light"
						bind:value={month}
						on:change={() => {
							switchmonth(month);
							calcall;
						}}
					>
						<option class="dropdown-item" value="jan">January</option>
						<option class="dropdown-item" value="feb">February</option>
						<option class="dropdown-item" value="mar">March</option>
						<option class="dropdown-item" value="apr">April</option>
						<option class="dropdown-item" value="may">May</option>
						<option class="dropdown-item" value="jun">June</option>
						<option class="dropdown-item" value="jul">July</option>
						<option class="dropdown-item" value="aug">August</option>
						<option class="dropdown-item" value="sep">September</option>
						<option class="dropdown-item" value="oct">October</option>
						<option class="dropdown-item" value="nov">November</option>
						<option class="dropdown-item" value="dec">December</option>
					</select>
				</div>
				<div class="mt-4 float-start"><p>Total Price : {$sp}</p></div>
			</div>
			<div class="float-end">
				<div class="">
					<button class="w-40 bg-secondary fs rounded-3 p-1 text-light float-end" on:click={clearsp}
						>Clear</button
					>
				</div>
				<div class="">
					<button
						class="w-40 mt-4 mb-1 rounded-3 fs bg-secondary text-center mt-1 text-light text-light"
						on:click={() => {
							check31(i);
						}}
						><h3>+</h3>
					</button>
				</div>
			</div>
		</div>
	</div>
	<table class="bg-dark text-light mt-3 w-19">
		<tr>
			<th class="border border-2">From</th>
			<th class="border border-2">To</th>
			<th class="border border-2">$&nbsp;/&nbsp;L</th>
			<th class="border border-2">Liters</th>
			<th class="border border-2">Price</th>
		</tr>

		{#each { length: i } as _, tt}
			{#if showw[tt]}
				<tr>
					<td class="border border-2">
						{#if tt >= 1}
							<select
								name="gg"
								class="btn fs w-40 mid bg-dark text-light"
								id="val1"
								bind:value={dayvar1[tt]}
								on:change={calcall}
							>
								{#each { length: $daysinmonth } as b, j}
									{#if tt - 1 >= 0}
										{#if j + 1 > dayvar2[tt - 1] && j + 1 <= $daysinmonth}
											<option class="dropdown-item" value={j + 1}>{j + 1}</option>
										{/if}
									{/if}
								{/each}
							</select>
						{:else}<select
								name="gg"
								class="btn fs w-40 mid bg-dark text-light"
								id="val1"
								bind:value={dayvar1[tt]}
								on:change={calcall}
							>
								<option class="dropdown-item" value={1}>1</option>
							</select>{/if}</td
					>
					<td class="border border-2"
						><select
							class="btn fs w-40 mid text-center bg-dark text-light"
							name="gg2"
							id="val2"
							bind:value={dayvar2[tt]}
							on:change={calcall}
						>
							<option value="0" />
							{#each { length: $daysinmonth + 1 } as b, j}
								{#if dayvar1[tt]}
									{#if j + 1 > dayvar1[tt]}
										<option class="dropdown-item" value={j}>{j}</option>
									{/if}
								{/if}
							{/each}
						</select></td
					>
					<td class="border border-2"
						><div class="text-center mid w-40 number-container">
							<input
								class="dynamic-number cform-control mid w-40 bg-dark text-light"
								id="email"
								placeholder="price of milk"
								name="email"
								bind:value={ppl[tt]}
								on:change={calcall}
							/>
						</div></td
					>
					<td class="border border-2"
						><div class="text-center mid w-40 number-container">
							<input
								class="dynamic-number cform-control mid w-40 bg-dark text-light"
								id="pwd2"
								placeholder="liters of milk"
								name="pswd"
								bind:value={lpd[tt]}
								on:change={calcall}
							/>
						</div>
					</td>
					<td class="border border-2 w-40 px-1 fsm text-center">
						<div class="number-container text-center">
							<span class="dynamic-number text-center">{$tp[tt]}</span>
						</div></td
					>
				</tr>
			{/if}
		{/each}
	</table>
</div>

<style>
	.number-container {
		max-width: 15vw; /* Set your maximum width */
	}

	.dynamic-number {
		word-wrap: break-word; /* Break the number into multiple lines if it exceeds the width */
	}
	.fsm {
		font-size: 15px;
		font-family: sans-serif;
	}
	.left {
		text-align: left;
	}
	.w-19 {
		width: 95vw;
		text-align: center;
		align-self: center;
		align-content: center;
		align-self: center;
		vertical-align: middle;
		margin-left: 2.5vw;
		margin-right: 2.5vw;
	}
	.w-40 {
		width: 20vw;
	}
	.mid {
		display: inline-block;
		vertical-align: middle;
		align-items: center;
	}

	.fs {
		padding: 0 0 0 0;
		background: none;
		border: 0;
	}
	.fs:focus {
		outline: 0;
	}
	.cform-control:focus {
		outline: 0;
	}
	.cform-control::-webkit-date-and-time-value {
		height: 1.5em;
	}
	.cform-control::-moz-placeholder {
		color: #6c757d;
		opacity: 1;
	}
	.cform-control::placeholder {
		color: #6c757d;
		opacity: 1;
	}
	.cform-control:disabled {
		background-color: #e9ecef;
		opacity: 1;
	}
	.cform-control::-webkit-file-upload-button {
		padding: 0.375rem 0.75rem;
		margin: -0.375rem -0.75rem;
		-webkit-margin-end: 0.75rem;
		margin-inline-end: 0.75rem;
		color: #212529;
		background-color: #e9ecef;
		pointer-events: none;
		border-color: inherit;
		border-style: solid;
		border-width: 0;
		border-inline-end-width: 1px;
		border-radius: 0;
		-webkit-transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
			border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
		transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
			border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
	}
	.cform-control::file-selector-button {
		padding: 0.375rem 0.75rem;
		margin: -0.375rem -0.75rem;
		-webkit-margin-end: 0.75rem;
		margin-inline-end: 0.75rem;
		color: #212529;
		background-color: #e9ecef;
		pointer-events: none;
		border-color: inherit;
		border-style: solid;
		border-width: 0;
		border-inline-end-width: 1px;
		border-radius: 0;
		transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
			border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
	}
	@media (prefers-reduced-motion: reduce) {
		.cform-control::-webkit-file-upload-button {
			-webkit-transition: none;
			transition: none;
		}
		.cform-control::file-selector-button {
			transition: none;
		}
	}
	.cform-control:hover:not(:disabled):not([readonly])::-webkit-file-upload-button {
		background-color: #dde0e3;
	}
	.cform-control:hover:not(:disabled):not([readonly])::file-selector-button {
		background-color: #dde0e3;
	}

	.cform-control {
		display: block;
		width: 100%;
		padding: 0.1rem 0.1rem;
		font-size: 1rem;
		font-weight: 400;
		line-height: 1.5;
		color: #212529;
		background: none;
		border: 0px solid #ced4da;
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;
		border-radius: 0.375rem;
		transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
	}
</style>
