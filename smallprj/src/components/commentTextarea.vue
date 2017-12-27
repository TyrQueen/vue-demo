<template>

	<!--<comment-textarea v-bind:type="type" v-bind:name="oldComment" v-on:submit="addComment" v-on:cancel="cancelCommit">-->

	<!--<comment-textarea v-bind:type="type" v-on:submit="addComment">

    <div class="commentBox">
      <h3>发表评论</h3>

      <p v-if="type">回复&nbsp;{{name}}</p>

      <textarea name="" value="请填写评论内容" v-model="commentText"></textarea>

      <button class="btn" v-on:click="addComment">发表</button>

      <button class="btn" v-on:click="cancelComment">取消</button>


    </div>

  </comment-textarea>-->

	<div class="commentBox">
		<h3>发表评论</h3>
		<textarea name="" value="请填写评论内容" v-model="commentText"></textarea>
		<button class="btn" v-on:click="addComment">发表</button>
		<!--<button class="btn" v-on:click="canelComment">取消</button>-->
	</div>


</template>

<script>
export default {
    name: 'comment-textarea',

    props: ['name'],
    
    data: function() {
    return {
      commentText:""
      }
    },
    
    methods: {
		addComment: function() {
            this.$emit("submit ",this.commentText);
			this.commentText = " ";
		}
	}
}
</script>

<style scoped>
	.commentBox {
		margin: 20px;
	}
	
	.commentBox h3 {
		color: #634322;
		background: #e9e5df;
		padding: 8px 15px;
		text-align: left;
		font-size: 16px;
	}
	
	.commentBox textarea {
		overflow: auto;
		width: 100%;
		height: 95px;
		outline: none;
		resize: none;
	}
	
	.commentBox button {
		float: right;
		margin-left: 20px;
		padding: 5px 30px;
		background: #01553D;
		border-radius: 5px;
		color: #fff;
		font-size: 16px;
	}
	
	.commentBox button:hover {
		color: #fff;
		background: #047857
	}
	
	.btn-search {
		border: 0;
		position: absolute;
		width: 19px;
		height: 19px;
		top: 21%;
		right: 5%;
		padding: 0;
		outline: none;
		box-shadow: none;
	}
	
	.btn-search:hover {
		background-color: #fff;
	}
	
	.btn-envelope {
		background: #01553D;
		display: block;
		margin: 0.5em auto 0;
		color: #fff;
	}
	
	.btn-envelope:hover {
		background: #047857;
		color: #fff;
	}
	
	.btn-envelope span {
		margin-right: 0.3em;
	}
</style>