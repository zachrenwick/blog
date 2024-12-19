<script>
	import '@evidence-dev/tailwind/fonts.css';
	import '../app.css';
	import { EvidenceDefaultLayout } from '@evidence-dev/core-components';
	export let data;

    import { onMount } from 'svelte';
// Dynamically import the Google Tag Manager script
onMount(async () => {
    const gtagScript = document.createElement('script');
    gtagScript.src = "https://www.googletagmanager.com/gtag/js?id=G-SH8P4T8C3W";
    gtagScript.async = true;
    document.head.appendChild(gtagScript);

    gtagScript.onload = () => {
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-SH8P4T8C3W');
    };
});


</script>

<EvidenceDefaultLayout {data}>
	<slot slot="content" />
</EvidenceDefaultLayout>