<script>
	import { onMount } from 'svelte';
	// import moment from 'moment';
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
