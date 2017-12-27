<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>


    <div class="rightBox" id="comment">

      <comment-content v-bind:comment="comment" v-on:change="changCommmer">

      </comment-content>

      <comment-textarea v-bind:name="oldComment" v-on:submit="addComment">

      </comment-textarea>


    </div>
  </div>

</template>

<script>

import HelloWorld from './components/HelloWorld';
import commentTextarea from './components/commentTextarea';
import commentContent from './components/commentContent';

export default {

	
	name: 'app',


	components: {
		HelloWorld,
    	commentTextarea,
		commentContent
  	},
  data: {
		commenter: "Silver",   //评论人
		
		oldComment: null,
		comment: [
			{
				name: "Silver",
				time: "2017-12-27",
				content: "111",
			
			},
			{
				name: "Black",
				time: "2017-12-27",
				content: "222",
			
			}
		]
	},
	methods: {
		addComment: function(data) {
		
				this.comment.push({
					name: 'Silver',
					time: getTime(),
					content: data,
				
				});	
			
		},

		changCommmer: function(name,index) {
			this.oldComment = name;
			this.chosedIndex = index;
		}
	}
  
}

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .rightBox {
    background: #fff;
    padding-bottom: 2em;
    padding-top: 5px;
  }

  .comment {
    margin-bottom: 15px;
  }

  .comment+.comment,
  .reply+.reply {
    border-top: 1px solid #ccc;
  }

  .comment b {
    color: #01553D;
    font-size: 16px;
    display: block;
    margin: 5px 0;
  }

  .comment b span {
    color: #333;
    font-size: 14px;
    margin-left: 20px;
  }

  .comment p {
    font-size: 16px;
    color: #333;
  }

</style>
