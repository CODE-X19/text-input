<template>
  <div class="container">
    <h4>A message you want to send</h4>

    <form @submit.prevent="submitForm">
      <input type="text" placeholder="enter your message" v-model="message" class="box">
      <input type="submit" value="Send" class="button">
    </form>

    <h5 class="feedback" :class="{ 'show': feedbackVisible }">Please enter a message to send</h5>
    <h3 v-if="messageSent">Message delivered!</h3>
    <h4 class="message-content" v-if="messageSent">{{ messageContent }}</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      feedbackVisible: false,
      messageSent: false,
      messageContent: ''
    };
  },
  methods: {
    submitForm() {
      if (this.message === '') {
        this.feedbackVisible = true;
        setTimeout(() => {
          this.feedbackVisible = false;
        }, 4000);
      } else {
        this.messageContent = this.message;
        this.message = '';
        this.messageSent = true;
      }
    }
  }
};
</script>

<style>
*{
    margin:0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'poppins','sans-seri';
}
body{
    background-image: url(ball.jpg );
    background-size: 100%;
   background-repeat: no-repeat;    
}
body,html{
   
     display: grid;
    height: 100%; 
    place-items: center; 
}

h4{
    font-size: 1.5rem;
    margin-bottom: .5rem;
    font-family: inherit;
    font-weight: 500;
    line-height: 1.2;
    text-transform: capitalize;
}
.container{
    width:600px;
    background-color: rgb(255, 255, 255);
    padding: 25px 30px;
    border-radius: 10px;
    box-shadow: 5px 5px 20px rgba(0,0,0,0.2);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
}
form{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center; 
    width: 100%; 
}
form input{
    margin: 10px 0;
    outline: none;
    border: none ;
    background-color: #faeb98;
}

form input.box{
    width: 500px;
    
    height: 40px;
    font-size: 1.2rem;
    padding: 0 10px;
    border-radius: 10px;
}

form input.button{
    font-size: 1rem;
    padding: 12px 20px;
    background-color: #642f03;
    color: aliceblue;
    font-weight: 500;
    cursor: pointer;
    border-radius: 10px;
    border:none ;
}
h5{
    background-color: #dbbb07;
    font-size: 1.2rem;
    width: 100%;
    padding: 10px 0;
    border-radius: 10px;

}
.feedback{
    display: none;
}
.show{
    display: block;
}
.message-content{
    color: #583b03;
    font-weight: bold;
    font-size: 1.2rem;
}
</style>
