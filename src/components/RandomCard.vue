import Vue from 'vue'; export default Vue.extend({ props: { rows: { type:
Number, default: 5 }, cols: { type: Number, default: 5 }, }, data() { return {
avaailableCharacters: `ABCDEFGHIJKLMNOPQRSTUVWXYZ`, }; }, computed: {
totalCount(): number { return this.rows * this.clos; }, shuffledCharacters():
string[] { let characters = this.avaailableCharacters.split(""); let length =
characters.length; for(let i = length - 1; i > 0; i--) { let j =
Math.floor(Math.random() * (i + 1)); let tmp = characters[i]; characters[i] =
characters[j]; characters[j] = tmp; } return characters; }, }, mounted(): void {
}, methods: { }, });
