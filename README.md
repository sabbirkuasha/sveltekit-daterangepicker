# sveltekit-dateRangePicker

Checkout Demo [`sveltekit-dateRangePicker`](https://sveltekit-daterangepicker.vercel.app/).

## Step by step guide

- Install sveltekit [`sveltekit install guide`](https://www.sabbirz.com/blog/install-sveltekit-efficientlysvelte-kit--vite-).
- Install daterangepicker & moment

```bash
# install daterangepicker
npm i daterangepicker

# install moment
npm i moment
```

- DateRangePicker uses Jquery but we will skip using Jquery and we will do it, using tools provided by sveltekit
- Import onMount and daterangepicker

```js
import { onMount } from 'svelte';
import moment from 'moment'; //this actually have no use, you can understand later
import daterangepicker from 'daterangepicker';
```

- Let's create 2 variables, one to target html markup and another to hold the selected date

```js
let dateContainerID = '#dateRange';
let DateSelected = '';
```

- Let's write onMount functiont

```js
onMount(() => {
	const options = {
		startDate: moment().subtract(6, 'days'),
		endDate: moment(),
		opens: 'right',
		alwaysShowCalendars: true,
		ranges: {
			'Last 7 Days': [moment().subtract(6, 'days'), moment()],
			'Last 30 Days': [moment().subtract(29, 'days'), moment()],
			'This Month': [moment().startOf('month'), moment().endOf('month')],
			'Last Month': [
				moment().subtract(1, 'month').startOf('month'),
				moment().subtract(1, 'month').endOf('month')
			]
		}
	};

	const picker = new daterangepicker(dateContainerID, options, (start, end) => {
		DateSelected = start.format('YYYY-MM-DD') + ' to ' + end.format('YYYY-MM-DD');
		console.log('New date range selected: ' + DateSelected);
	});
});
```

- Let's write the markup

```html
<main>
	<div class="m-auto text-center my-5">
		<input type="text" id="dateRange" value="" class="w-1/2 bg-orange-700 text-white font-bold" />
	</div>
</main>
```

- So the complete code will be looks like this

```Js
<script>
	import { onMount } from 'svelte';
	import moment from 'moment';
	import daterangepicker from 'daterangepicker';

	let dateContainerID = '#dateRange';
	let DateSelected = '';

	onMount(() => {
		const options = {
			startDate: moment().subtract(6, 'days'),
			endDate: moment(),
			opens: 'right',
			alwaysShowCalendars: true,
			ranges: {
				'Last 7 Days': [moment().subtract(6, 'days'), moment()],
				'Last 30 Days': [moment().subtract(29, 'days'), moment()],
				'This Month': [moment().startOf('month'), moment().endOf('month')],
				'Last Month': [
					moment().subtract(1, 'month').startOf('month'),
					moment().subtract(1, 'month').endOf('month')
				]
			}
		};

		const picker = new daterangepicker(dateContainerID, options, (start, end) => {
			DateSelected = start.format('YYYY-MM-DD') + ' to ' + end.format('YYYY-MM-DD');
			console.log('New date range selected: ' + DateSelected);
		});
	});
</script>

<main>
	<div class="m-auto text-center my-5">
		<input type="text" id="dateRange" value="" class="w-1/2 bg-orange-700 text-white font-bold" />
	</div>
</main>

```

- Run

```bash
npm run dev -- --host
```

- You will find an error, stating that momentjs is not a function LOL
- Remove moment from script tag

```js
import { onMount } from 'svelte';
//	import moment from 'moment';
import daterangepicker from 'daterangepicker';
```

> Check **package.json** for **moment js** version number & then find the minified CDN version & then paste it inside **head** tag & don't forget **dateRangePicker CSS** file too

```html
<!-- for date range picker -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.4/moment.min.js"></script>
<link
	rel="stylesheet"
	type="text/css"
	href="https://cdn.jsdelivr.net/npm/daterangepicker/daterangepicker.css"
/>
```

- DONE
