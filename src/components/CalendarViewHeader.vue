<template>
	<div class="cv-header">
		<div class="cv-header-nav">
			<img
				:disabled="!headerProps.previousYear"
				class="previousPeriod"
				aria-label="Previous Period"
				:src="previousYearLabel"
				@click.prevent="onInput(headerProps.previousYear)"
			/>
			<img
				:disabled="!headerProps.previousPeriod"
				class="previousPeriod"
				aria-label="Previous Period"
				@click.prevent="onInput(headerProps.previousPeriod)"
				:src="previousPeriodLabel"
			/>
			<button
				class="currentPeriod"
				aria-label="Current Period"
				@click.prevent="onInput(headerProps.currentPeriod)"
			>
				{{ headerProps.currentPeriodLabel }}
			</button>
			<img
				:src="nextPeriodLabel"
				:disabled="!headerProps.nextPeriod"
				class="nextPeriod"
				aria-label="Next Period"
				@click.prevent="onInput(headerProps.nextPeriod)"
			/>
			<img
				:src="nextYearLabel"
				:disabled="!headerProps.nextYear"
				class="nextYear"
				aria-label="Next Year"
				@click.prevent="onInput(headerProps.nextYear)"
			/>
		</div>
		<div class="periodLabel">
			<slot name="label">{{ headerProps.periodLabel }}</slot>
		</div>
	</div>
</template>
<script>
export default {
	name: "CalendarViewHeader",
	props: {
		headerProps: {
			type: Object,
			required: true,
		},
		previousYearLabel: { type: String, default: "<<" },
		previousPeriodLabel: { type: String, default: "<" },
		nextPeriodLabel: { type: String, default: ">" },
		nextYearLabel: { type: String, default: ">>" },
	},
	methods: {
		onInput(d) {
			this.$emit("input", d)
		},
	},
}
</script>
<style>
.nextYear {
	cursor: pointer;
	margin-right: 12px;
}

.nextPeriod {
	cursor: pointer;
	margin-right: 12px;
}

.previousPeriod {
	cursor: pointer;
	margin-right: 12px;
}

.previousYear {
	cursor: pointer;
	margin-right: 12px;
}

.cv-header {
	display: flex;
	flex: 0 1 auto;
	flex-flow: row nowrap;
	align-items: center;
	min-height: 2.5em;
	border-width: 1px 1px 0 1px;
}

.cv-header .periodLabel {
	display: flex;
	flex: 1 1 auto;
	flex-flow: row nowrap;
	min-height: 1.5em;
	line-height: 1;
	font-size: 1.5em;
}

.cv-header,
.cv-header button {
	border-style: solid;
	border-color: #ddd;
}

.cv-header-nav,
.cv-header .periodLabel {
	margin: 0.1em 0.6em;
}

.cv-header-nav button,
.cv-header .periodLabel {
	padding: 0.4em 0.6em;
}

.cv-header button {
	box-sizing: border-box;
	line-height: 1em;
	font-size: 1em;
	border-width: 1px;
}
</style>
