<script>
	import { writable } from 'svelte/store';
	const date = new Date();
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
	let day1 = [];
	let day2 = [];
	let ppll = [];
	let lpdl = [];
	let ml;
	let showw = [];
	let myModal;
	for (let y = 0; y < 32; y++) {
		dayvar1.push(0);
		dayvar2.push(0);
		ppl.push(0);
		nod.push(0);
		lpd.push(0);
		$tp.push(0);
		day1.push(0);
		day2.push(0);
		lpdl.push(0);
		ppll.push(0);
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
		ml.disabled = true;
	}
	function calcall() {
		for (let ca = 0; ca < i; ca++) {
			calc(ca);
			update(ca);
		}
	}
	function calc(ii) {
		nod[ii] = dayvar2[ii] - dayvar1[ii] + 1;
		$tp[ii] = lpd[ii] * nod[ii] * ppl[ii];
		day1[ii].disabled = true;
		day2[ii].disabled = true;
		lpdl[ii].disabled = true;
		ppll[ii].disabled = true;
	}
	function clearsp() {
		sp.set(0);
		location.reload();
	}
	function update(ii) {
		sum = 0;
		sum = sum + $tp[ii];
		sp.set(sum);
	}
	const reg = /^([1-9]|[1-2][0-9]|3[0-1])$/;
	function check31(e) {
		if (dayvar2[e - 1] != 31 && reg.test(dayvar2[e - 1])) {
			i++;
		} else {
			alert(
				'You cannot create a situation because you reached the end of the month or you have not entered a day.'
			); //asdfXXXV2020 1555@januaryshellxngxcbiag5+🐔SnSnSnKHBHecolombia🌖lingo🐛🐛🐛🐛🐛🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️🏋️‍♂️i am loved
		}
	}
</script>

<div class="text-center mid">
	<div class="card border border-3 bg-dark mx-auto mt-2 mb-2 w-19">
		<div class="text-center text-light card-header">
			<h3>Milk price calculator</h3>
		</div>
		<div class="card-body row">
			<div class="col w-100 mid">
				<p class="text-center w-100 mid">Total Price: {$sp}</p>
				<select
					name="gg3"
					id="val3"
					class="form-select mid w-100 text-center bg-dark text-light border border-2"
					bind:value={month}
					on:change={() => {
						switchmonth(month);
					}}
					bind:this={ml}
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

			<div class="text-center mid float-end col row">
				<div class="col text-center w-100">
					<button
						class="w-40 rounded-3 mb-1 bg-secondary text-center mt-1 text-light"
						on:click={calcall}>C</button
					>

					<button
						class="w-40 rounded-3 mb-1 bg-secondary text-center mt-1 text-light"
						on:click={clearsp}>CTP</button
					>
				</div>
				<div class="col text-center w-100">
					<button
						class="w-40 mb-1 rounded-3 bg-secondary text-center mt-1 text-light text-light"
						on:click={() => {
							check31(i);
						}}>AS</button
					>

					<button class="w-40 rounded-3 mb-1 bg-secondary text-center mt-1"
						><a href="/help" class=" text-light">Help</a></button
					>
				</div>
			</div>
		</div>
	</div>

	<table class="table mt-2 bg-dark text-light w-19">
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
								bind:this={day1[tt]}
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
								bind:this={day1[tt]}
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
							bind:this={day2[tt]}
						>
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
						><div class="text-center mid w-40">
							<input
								class="cform-control mid w-40 bg-dark text-light"
								id="email"
								placeholder="price of milk"
								name="email"
								bind:value={ppl[tt]}
								bind:this={ppll[tt]}
							/>
						</div></td
					>
					<td class="border border-2"
						><div class="text-center mid w-40">
							<input
								class="cform-control mid w-40 bg-dark text-light"
								id="pwd2"
								placeholder="liters of milk"
								name="pswd"
								bind:value={lpd[tt]}
								bind:this={lpdl[tt]}
							/>
						</div>
					</td>
					<td class="border border-2 w-40">{$tp[tt]}</td>
				</tr>
			{/if}
		{/each}
	</table>
</div>

<style>
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

	/*.cbtn {
		--bs-btn-padding-x: 0.75rem;
		--bs-btn-padding-y: 0.375rem;
		--bs-btn-font-family: ;
		--bs-btn-font-size: 1rem;
		--bs-btn-font-weight: 400;
		--bs-btn-line-height: 1.5;
		--bs-btn-color: #212529;
		--bs-btn-bg: transparent;
		--bs-btn-border-width: 1px;
		--bs-btn-border-color: transparent;
		--bs-btn-border-radius: 0.375rem;
		--bs-btn-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.15), 0 1px 1px rgba(0, 0, 0, 0.075);
		--bs-btn-disabled-opacity: 0.65;
		--bs-btn-focus-box-shadow: 0 0 0 0.25rem rgba(var(--bs-btn-focus-shadow-rgb), 0.5);
		display: inline-block;
		padding: var(--bs-btn-padding-y) var(--bs-btn-padding-x);
		font-family: var(--bs-btn-font-family);
		font-size: var(--bs-btn-font-size);
		font-weight: var(--bs-btn-font-weight);
		line-height: var(--bs-btn-line-height);
		color: var(--bs-btn-color);
		text-align: center;
		text-decoration: none;
		vertical-align: middle;
		cursor: pointer;
		-webkit-user-select: none;
		-moz-user-select: none;
		user-select: none;
		border: var(--bs-btn-border-width) solid var(--bs-btn-border-color);
		border-radius: var(--bs-btn-border-radius);
		background-color: var(--bs-btn-bg);
		transition: color 0.15s ease-in-out, background-color 0.15s ease-in-out,
			border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
	}*/
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
