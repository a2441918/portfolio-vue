<template>
    <div class='row item'>
        <div class='twelve columns'>
            <h3>
                <a :href="entry.website">{{entry.name}}</a>
            </h3>
            <p class='info'>
                <span class='info-summary'>{{entry.summary}}</span>
            </p>
        </div>
    </div>
</template>

<script>
	export default {
		name: 'PortfolioEntry',
		props: ['entry']
	};
</script>
