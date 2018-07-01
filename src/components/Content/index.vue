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
				td.subcolor {{client.type.title}}
				td.subcolor {{client.company}}
				td.subcolor {{client.country}}
				td.maincolor {{client.subscription}}
				td
					button.edit(type='button', @click='editClient(client)') &#9998
		button.content__btn(type='button', @click='') SHOW MORE
		edit-user.modal-edit(v-if='isShowModal', @closeModal='closeEditModal')
			template(slot='header')
				.modal-edit__header
					.modal-edit__header-info
						.modal-edit__header-title Edit {{selectedClient.firstName}}
						.modal-edit__header-id unique ID - {{selectedClient.id}}
					.modal-edit__close
						button.modal-edit__close-btn(type='button', @click='isShowModal = false') &#9587
			template(slot='body')
				.modal-edit__body
					form.edit-form
						.edit-form__row
							.edit-form__group
								label.edit-form__label(for='email') E-mail
								input.edit-form__input#email(type='email', :disabled='isDisable', v-model='selectedClient.email')
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='firstName') First name
								input.edit-form__input#firstName(type='text', :disabled='isDisable', v-model='selectedClient.firstName')
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='lastName') Last Name
								input.edit-form__input#lastName(type='text', :disabled='isDisable', v-model='selectedClient.lastName')
						.edit-form__row
							.edit-form__group
								label.edit-form__label(for='country') Country
								input.edit-form__input#country(type='text', :disabled='isDisable', v-model='selectedClient.country')
							.edit-form__group
								label.edit-form__label(for='company') Company
								input.edit-form__input#company(type='text', :disabled='isDisable', v-model='selectedClient.company')
						.edit-form__row
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='type') Type
								select.edit-form__input#type(v-model='selectedClient.type.title')
									option Business
									option Private
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='level') Level
								select.edit-form__input#level(v-model='selectedClient.level')
									option(v-for='n in 12') {{n}}
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='validated') validated
								input.edit-form__input#validated(type='text', v-model.trim='selectedClient.validated')
							.edit-form__group.edit-form__group--width
								label.edit-form__label(for='coins') coins
								input.edit-form__input#coins(type='number', v-model.number='selectedClient.coins')
			template(slot='footer')
				.modal-edit__footer
					.modal-edit__footer-info
						.modal-edit__footer-desc Subscription type - #[span.text-orange {{selectedClient.type.cost}}]
						.modal-edit__footer-desc Subscription date - #[span.text-orange {{selectedClient.subscription}}]
					ul.modal-edit__footer-actions
						li.modal-edit__footer-btn
							button.edit-form__btn(type='button', :disabled='isDisable', @click='') Reset password
						li.modal-edit__footer-btn
							button.edit-form__btn(type='button', :disabled='isDisable', @click='') Revoke access
						li.modal-edit__footer-btn
							button.edit-form__btn(type='button', @click='') Save
</template>

<script>
export default {
	name: 'Content',
	components: {
		EditUser: () => import('@/components/Modal')
	},
	data () {
		return {
			clients: [
				{
					id: '1asd51as23',
					email: 'leffler.karelle@marcellus.net',
					firstName: 'Daniel',
					lastName: 'Taylor',
					country: 'Korea',
					company: 'green',
					type: {
						title: 'Business',
						cost: '99.99'
					},
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
					type: {
						title: 'Private',
						cost: '59.99'
					},
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
					type: {
						title: 'Business',
						cost: '99.99'
					},
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
					type: {
						title: 'Private',
						cost: '59.99'
					},
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
					type: {
						title: 'Business',
						cost: '99.99'
					},
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
					type: {
						title: 'Private',
						cost: '59.99'
					},
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
					type: {
						title: 'Business',
						cost: '99.99'
					},
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
					type: {
						title: 'Private',
						cost: '59.99'
					},
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
					type: {
						title: 'Private',
						cost: '59.99'
					},
					level: '3',
					validated: 'Yes',
					coins: 3000,
					subscription: '11/02/2016'
				}
			],
			selectedClient: {},
			isShowModal: false,
			isDisable: true
		}
	},
	methods: {
		editClient (client) {
			this.selectedClient = client
			this.isShowModal = true
		},
		closeEditModal () {
			this.isShowModal = false
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
.modal-edit__header {
	display: flex;
	justify-content: space-between;
	padding: 20px;
	background-color: #fff;
}
.modal-edit__close-btn {
	background: 0;
	border: 0;
	color: rgba(#b5b5b8, .7);
	font-size: 18px;
	display: inline-block;
	font-weight: 700;
	&:hover, &:active, &:focus {
		color: #b5b5b8;
	}
}
.modal-edit__header-title {
	color: var(--brandOrange);
	text-transform: uppercase;
	font-size: 18px;
	margin-bottom: 8px;
}
.modal-edit__body {
	background-color: var(--bodyColor);
	padding: 10px;
}
.edit-form__row {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
}
.edit-form__group {
	margin: 10px;
	width: 410px;
	&--width {
		width: 195px;
	}
}
.edit-form__label {
	display: block;
	margin-bottom: 10px;
	font-size: 14px;
	text-transform: uppercase;
}
.edit-form__input {
	box-shadow: 0 1px 8px rgba(229, 229, 235, 0.5);
	border-radius: 5px;
	border: 1px solid rgba(223, 223, 230, 0.8);
	background-color: #fff;
	padding: 17px;
	font-size: 14px;
	width: 100%;
	&:disabled {
		font-weight: 300;
		color: #a2a2a6;
	}
}
.modal-edit__footer {
	background-color: var(--bodyColor);
	padding: 10px 20px;
	display: flex;
	justify-content: space-between;
}
.modal-edit__footer-desc {
	margin: 5px 0;
}
.modal-edit__footer-actions {
	display: flex;
}
.modal-edit__footer-btn {
	margin-right: 10px;
	&:last-child {
		margin-right: 0;
	}
}
.text-orange {
	color: var(--brandOrange);
	font-weight: 700;
}
.edit-form__btn {
	box-shadow: 0 2px 4px rgba(230, 230, 232, 0.3);
	border-radius: 4px;
	border: 1px solid #61a970;
	background-color: var(--brandGreen);
	font-size: 14px;
	text-transform: uppercase;
	min-width: 110px;
	padding: 15px;
	color: #fff;
	&:disabled {
		background-color: var(--disabledColor);
		border: 1px solid var(--disabledColor);
	}
}
</style>
