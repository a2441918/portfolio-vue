<template>
    <section id='about'>
        <div class='row'>
            <div class='two columns'>
                <img class='profile-pic' src="../../assets/images/profile.jpg" :alt="name"/>
            </div>
            <div class='ten columns main-col'>
                <h2>About Me</h2>
                <p v-for="(summ, index) in summary" :key="`summ-${index}`">{{summ}}</p>
                <div class='row'>
                    <div class='columns contact-details'>
                        <h2>Contact Details</h2>
                        <p class='address'>
                            <span>{{location.city}}</span>
                            <br/>
                            <span>{{location.region + ', ' + location.postalCode}}</span>
                            <br/>
                            <span>{{location.countryCode}}</span>
                            <br/>
                            <a :href="'skype:' + basics.phone">
                                <span>{{basics.phone}}</span>
                            </a>
                            <br/>
                            <a :href="'mailto:' + basics.email">
                                <span>{{basics.email}}</span>
                            </a>
                        </p>
                    </div>
                    <div class='columns download'>
                        <p>
                            <a href="../../assets/ArunManoharResume.pdf" download='Arun-Manohar-Resume.pdf'
                               class='button'>
                                <i class='fa fa-download'></i>
                                Download Resume
                            </a>
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
	import {serverBus} from '../../main';

	export default {
		name: 'About',
		data() {
			return {
				name: '',
				location: {},
				summary: [],
				basics: {}
			};
		},
		created() {
			// Using the server bus
			serverBus.$on('resumeData', (data) => {
				this.basics = data.basics;
				this.name = data.basics.name;
				this.location = data.basics.location;
				this.summary = data.basics.summary.split('\n');
			});
		}
	};
</script>
