<template>
  <div class="home">
    <h1>Discord Webhook Creator</h1>
    
    <div class="bothSides">
      <div id="sideLeft" class="sideLeft">

        <div class="formsection">
          <div class="formgroup">
            <input v-model="webhook.url" class="inputfield inputfield-long" type="text" id="webhookUrl" spellcheck="false" placeholder="https://discordapp.com/api/webhooks/8691772/EO">
            <label for="webhookUrl" class="formlabel">Webhook URL</label>
          </div>  
        </div>

        <div class="formsection">
          <div class="formgroup">
            <input v-model="webhook.username" class="inputfield inputfield-short" type="text" id="username" spellcheck="false" placeholder="Welcome to the Jungle">
            <label for="username" class="formlabel">Username</label>
          </div>

          <div class="formgroup">
            <input v-model="webhook.avatarUrl" class="inputfield inputfield-med" type="text" id="avatarUrl" spellcheck="false" placeholder="Welcome to the Jungle">
            <label for="avatarUrl" class="formlabel">Avatar URL</label>
          </div>          
        </div>

        <div class="formsection">
          <div class="formgroup">
            <input v-model="webhook.content" class="inputfield inputfield-long" type="text" id="content" spellcheck="false" placeholder="Welcome to the Jungle">
            <label for="content" class="formlabel">Content</label>
          </div>  
        </div> 


        <div class="formsection">
          <div class="formgroup">
            <input v-model="webhook.embed.title" class="inputfield inputfield-short" type="text" id="embedTitle" spellcheck="false" placeholder="Welcome to the Jungle">
            <label for="embedTitle" class="formlabel">Title</label>
          </div>  
        </div>

        <div class="formsection">
          <button @click="sendWebhook">Send</button>
        </div>

      </div>

      <div class="sideRight">
        yeet
      </div>
    </div>


    <h1>In work fuccer</h1>
  </div>
</template>

<script>
const axios = require('axios')
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
      
  },
  data() {
    return {
      webhook: {
        embed: {}
      }
    }
  },
  methods: {
    sendWebhook() {
      /*
      axios.get(this.webhook.url)
      .then((response) => console.log(response));
      */
      axios.post(
        this.webhook.url, {
          "content": this.webhook.content,
          "username": this.webhook.username,
          "avatar_url": this.webhook.avatarUrl,
          "embeds": [
            {
              "title": this.webhook.embed.title,
              "description": this.webhook.embed.description,
              "url": this.webhook.embed.url,
              "timestamp": this.webhook.embed.timestamp,
              "color": this.webhook.embed.color,
              /*
              "footer": {
                "text": this.webhook.embed.footer.text,
                "icon_url": this.webhook.embed.footer.icon
              },
              "image": {
                "url": this.webhook.embed.image.url,
                "heigth": this.webhook.embed.image.heigth,
                "width": this.webhook.embed.image.width
              },
              "thumbnail": {
                "url": this.webhook.embed.thumbnail.url,
                "heigth": this.webhook.embed.thumbnail.heigth,
                "width": this.webhook.embed.thumbnail.width
              },
              "video": {
                "url": this.webhook.embed.video.url,
                "heigth": this.webhook.embed.video.heigth,
                "width": this.webhook.embed.video.width
              },
              "provider": {
                "name": this.webhook.embed.provider.name,
                "url": this.webhook.embed.provider.url
              },
              "author": {
                "name": this.webhook.embed.author.name,
                "url": this.webhook.embed.author.url,
                "icon_url": this.webhook.embed.author.icon
              },
              "fields": {
                "name": this.webhook.embed.fields.name,
                "value": this.webhook.embed.fields.value,
                "inline": this.webhook.embed.fields.inline
              } 
              */
            }
          ]
        }
      )
    }
  }
}
</script>

<style lang="scss">

.bothSides {
  position: relative;
  display: flex;
  flex-direction: row;
}

.sideLeft {
  width: 50%;
}

$color-primary-light: #f3324c;
$color-primary-dark: #8a133b;

/* Text Input */

.formsection {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
  margin: 1rem;
  padding-top: 0.5rem;
  padding-bottom: 1rem;
  background-color: rgb(100, 100, 100);
  border-radius: 0.5rem;
}

.formgroup {
  position: relative;
  padding: 15px 0 0;
}
  
.inputfield {
    width: 100%;
    border: 0;
    border-bottom: 2px solid black;
    outline: 0;
    font-size: 0.8rem;
    color: black;
    padding: 7px 0;
    background: transparent;
    transition: border-color 0.2s;
    background-color: rgb(190, 190, 190);
    border-radius: 0.3rem;
    
    &.inputfield-small {
      width: 11rem;
    }

    &.inputfield-med {
      width: 25rem;
    }
  
    &::placeholder {
      color: transparent;
      visibility: hidden;
    }
  
    /* Normal */
    &:placeholder-shown ~ .formlabel {
      font-size: 0.8rem;
      cursor: text;
      top: 0;
    }
  
    /* disabled */
    &:disabled {
      ~ .formlabel {
        opacity: 0.7;
        cursor: not-allowed;
      }
      opacity: 0.7;
      cursor: not-allowed;
    }
  
    /* Focussed/Active */
    &:focus {
      ~ .formlabel {
        position: absolute;
        top: 0;
        display: block;
        transition: 0.2s;
        font-size: 0.7rem;
        background: linear-gradient(to top right, $color-primary-dark,$color-primary-light);
        background-clip: text;
        -webkit-text-fill-color: transparent;
        font-weight:700;
      }
      padding-bottom: 6px;
      border-width: 3px;
      border-image: linear-gradient(
        to right,
        $color-primary-dark,
        $color-primary-light
      );
      border-image-slice: 1;
    }
  
}

.inputfield-long {
  position: relative;
  width: 75vh;
}

.formlabel {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 0.8rem;
  background: linear-gradient(to top right, $color-primary-dark,$color-primary-light);
  background-clip: text;
  -webkit-text-fill-color: transparent;
  font-weight: 600;
}

/* reset input */
.inputfield {
    &:required,&:invalid { box-shadow:none; }
}
</style>