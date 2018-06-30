<template lang="pug">
	main.content
		table.table
			tr
				th E-mail
				th Name
				th Type
				th Company
				th Country
				th Subscription
				th
			tr(v-for='client in clients', :key='client.id')
				td.maincolor {{client.email}}
				td #[span.maincolor {{client.firstName}}] #[span.subcolor {{client.lastName}}]
				td.subcolor {{client.type}}
				td.subcolor {{client.company}}
				td.subcolor {{client.country}}
				td.maincolor {{client.subscription}}
				td
					button.edit(type='button', @click='editClient(client)') &#9998
		button.content__btn(type='button', @click='') SHOW MORE
</template>

<script>
export default {
	name: 'Content',
	data () {
		return {
			clients: [
				{
					id: '1asd51as23',
					email: 'leffler.karelle@marcellus.net',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Korea',
					company: 'green',
					type: 'Business',
					level: '6',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd521as23',
					email: 'karolann_walker@yahoo.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Rwanda',
					company: 'black',
					type: 'Private',
					level: '1',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd351as23',
					email: 'lucile.mcdermott@yahoo.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Guam',
					company: 'green',
					type: 'Business',
					level: '2',
					validated: 'No',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd51a5s23',
					email: 'elfrieda_sanford@hagenes.co.uk',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Korea',
					company: 'black',
					type: 'Private',
					level: '1',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1a1sd51as23',
					email: 'daphney.okuneva@gmail.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Guam',
					company: 'green',
					type: 'Business',
					level: '5',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd51as263',
					email: 'ezequiel_rutherford@yahoo.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Jersey',
					company: 'red',
					type: 'Private',
					level: '1',
					validated: 'No',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd513as23',
					email: 'leffler.karelle@marcellus.net',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Djibouti',
					company: 'black',
					type: 'Business',
					level: '2',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '1asd561as23',
					email: 'karolann_walker@yahoo.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Jersey',
					company: 'blue',
					type: 'Private',
					level: '1',
					validated: 'No',
					coins: 3000,
					subscription: '11/02/2016'
				},
				{
					id: '12asd51as23',
					email: 'lucile.mcdermott@yahoo.com',
					firstName: 'Lewis',
					lastName: 'Taylor',
					country: 'Djibouti',
					company: 'black',
					type: 'Private',
					level: '3',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				}
			]
		}
	},
	methods: {
		editClient (client) {
			console.log(client)
		}
	}
}
</script>

<style lang="scss" scoped>
.content {
	background-color: var(--bodyColor);
	padding: 25px;
	overflow-x: auto;
}
.table {
	box-shadow: 0 1px 8px rgba(229, 229, 235, 0.5);
	border-radius: 4px;
	border: 1px solid rgba(223, 223, 230, 0.8);
	background-color: #fff;
	width: 100%;
	border-collapse: collapse;
	margin-bottom: 30px;
}
th, td {
	border: 1px solid #e5e5eb;
	margin: 0;
}
th {
	color: var(--brandOrange);
	font-size: 16px;
	font-weight: 400;
	text-align: left;
	padding: 15px 20px;
}
td {
	padding: 30px 20px;
	font-size: 14px;
	&:last-child {
		padding: 30px 5px;
		text-align: center;
	}
}
.maincolor {
	color: var(--textColor);
}
.subcolor {
	color: var(--textSubColor);
}
.edit {
	padding: 0;
	background: 0;
	border: 0;
	font-size: 16px;
	color: var(--textColor);
}
.content__btn {
	width: 100%;
	padding: 25px;
	text-align: center;
	box-shadow: 0 1px 8px rgba(229, 229, 235, 0.5);
	border-radius: 4px;
	border: 1px solid rgba(223, 223, 230, 0.8);
	background-color: #fff;
	color: var(--brandOrange);
	text-transform: uppercase;
	transition: .2s;
	&:hover, &:active, &:focus {
		background-color: var(--brandBlueLigten);
		color: #fff;
	}
}
</style>
