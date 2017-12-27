
<template>
  <div class="commentBox">
    <h3>评论</h3>

    <p v-if="comment.length==0">No Comment</p>

    <div v-else>
      <div class="comment" v-for="(item,index) in comment" v-bind:index="index">
        <b>{{item.name}}<span>{{item.time}}</span></b>
        <p>{{item.content}}</p>
        <div class="reply" v-for="reply in item.reply">
        </div>
      </div>
    </div>
  </div>

</template>

<script>
export default {

    name: 'comment-content',
    
    props: ['comment'],

    

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

  .reply {
    margin: 15px 0 15px 50px;
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
