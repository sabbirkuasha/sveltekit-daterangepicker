<script>
	import { onMount } from 'svelte';
	import jQuery from 'jquery';
	import moment from 'moment';
	import daterangepicker from 'daterangepicker';

	let dateContainerID = '#dateRange';

	let onChange;
	let DateSelected = '';
	// $: onChange(DateSelected);

	onMount(() => {
		jQuery(function () {
			let currentTime = moment().format('YYYY-MM-DD HH:mm:ss');
			console.log(currentTime);
			console.log(jQuery(daterangepicker));

			// jQuery(dateContainerID).daterangepicker(
			// 	{
			// 		startDate: '06/25/2023',
			// 		endDate: '07/01/2023'
			// 	},
			// 	function (start, end) {
			// 		DateSelected = start.format('YYYY-MM-DD') + ' to ' + end.format('YYYY-MM-DD');
			// 		console.log('New date range selected: ' + DateSelected);
			// 	}
			// );

			// jQuery(dateContainerID).daterangepicker(
			// 	{
			// 		ranges: {
			// 			opens: 'center',
			// 			Today: [moment(), moment()],
			// 			Yesterday: [moment().subtract(1, 'days'), moment().subtract(1, 'days')],
			// 			'Last 7 Days': [moment().subtract(6, 'days'), moment()],
			// 			'Last 30 Days': [moment().subtract(29, 'days'), moment()],
			// 			'This Month': [moment().startOf('month'), moment().endOf('month')],
			// 			'Last Month': [
			// 				moment().subtract(1, 'month').startOf('month'),
			// 				moment().subtract(1, 'month').endOf('month')
			// 			]
			// 		},
			// 		alwaysShowCalendars: true,
			// 		startDate: moment(),
			// 		endDate: moment(),
			// 		opens: 'right'
			// 	},
			// 	function (start, end) {
			// 		//child to parent - Sab
			// 		DateSelected = start.format('YYYY-MM-DD') + ' to ' + end.format('YYYY-MM-DD');
			// 		console.log(
			// 			'New date range selected: ' +
			// 				start.format('YYYY-MM-DD') +
			// 				' to ' +
			// 				end.format('YYYY-MM-DD')
			// 		);
			// 	}
			// );
		});
	});
</script>

<main>
	<div id="dateRange" />
	<p>Date selected: {DateSelected}</p>
</main>
