<!-- 
Generic get-json-but-has-no-html-component.
Usage:
<fetch-json url="/api/endpoint-full-of-json"> 
    <div slot-scope="{ json }"> 
        <p v-for="item in json">
            {{ item.property }}
        </p>
    </div>
</fetch-json>
-->

<script>
import Vue from 'vue';

export default Vue.extend({
	props: ['url'],

	data() {
		return {
			json: [],
		}
	},

	mounted() {
		axios.get(this.url).then((result) => {
			this.json = result.data;
		});
	},

	render(createElement) {
		return this.$scopedSlots.default({
			json: this.json,
		});
	},

});


</script>