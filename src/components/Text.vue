<template>
	<div class="container">
        <div class="comment">
            <!--<p>Message is: {{ text }}</p> -->
            <input v-model="text" id="text1" class="textinput" :class="{red: color}" placeholder="What's happening?">
			<div>{{ charLeft }}</div>
            <div>
                <div v-if="isMaxChar">
                    <button @click="saveMessage">Send</button>
                </div>
                <div v-else>
                    <p>Has excedit el limit de caracters</p>
                </div>
            </div>
            <p v-for="message in messages" class="center">
                {{message}}
            </p>
		</div> 
    </div>  
</template>

<script>
export default {
	data() {
		return {
			words: 280,
            text : "",
            color : false,
            messages : []
		};
	},
    methods: {
        saveMessage() {
            this.messages.push(this.text);
        }
    },
    computed: {
        charLeft() {
            return this.words - this.text.length;
        },
        isMaxChar() {
            if (this.text.length <= this.words) {
                this.color = "";
                return true;
			} else {
                this.color = true;
                return false;
			}
        }
    }
}
</script>

<style scoped>
	.container {
            max-width: 820px;
            margin: 0px auto;
            margin-top: 50px;
        }

        .comment {
            float: left;
            width: 100%;
            height: auto;
        }

        .commenter {
            float: left;
        }

        .commenter img {
            width: 35px;
            height: 35px;
        }

        .comment-text-area {
            float: left;
            width: 100%;
            height: auto;
        }

        .textinput {
            float: left;
            width: 100%;
            min-height: 75px;
            outline: none;
            resize: none;
            border: 1px solid grey;
        }
        .red {
            background-color: red;
        }
        .center {
            text-align:center;
        }
</style>