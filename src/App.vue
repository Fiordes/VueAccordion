<template>
  <div id="app">
    <header>
      <h1>
        Vue
        <span>CORDION</span>
      </h1>
    </header>
    <div class="faqs">
      <FAQ
        v-for="(faq, i) in faqs"
        :faq="faq"
        :index="i"
        :key="i"
        :open="faq.open"
        @toggleOpen="toggleOpen"
      />
    </div>
  </div>
</template>

<script>
import FAQ from "@/components/FAQ";
export default {
  name: "App",
  components: {
    FAQ
  },
  data() {
    return {
      faqs: [
        {
          question: "Who is your dady?",
          answer: "I dont know this",
          open: false
        },
        {
          question: "Who is your momy?",
          answer: "I dont know this, realy",
          open: false
        },
        {
          question: "Who is your sister?",
          answer: "I dont know this,its true",
          open: false
        }
      ]
    };
  },
  methods: {
    toggleOpen: function(index) {
      this.faqs = this.faqs.map((faq, i) => {
        if (index === i) {
          faq.open = !faq.open;
        } else {
          faq.open = false;
        }

        return faq;
      });
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #eeeeee;
  font-family: sans-serif;
}

header {
  background: #3c3c3c;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px 0;
}

header h1 {
  color: #eeeeee;
  font-size: 28px;
  font-weight: 300;
  text-transform: uppercase;
}

header h1 span {
  color: #56e3b5;
  font-weight: 900;
}

.faq {
  display: block;
  width: 100%;
  max-width: 768px;
  margin: 15px auto;
  padding: 15px;
  border-radius: 8px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  background: #fff;
}

.faq .question {
  position: relative;
  color: #3c3c3c;
  font-size: 20px;
  transition: all 0.4s linear;
}

.faq .question::after {
  content: "";

  position: absolute;
  top: 50%;
  right: 0;
  transform: translateY(-50%) rotate(0deg);

  width: 30px;
  height: 30px;
  background-image: url("./assets/arrow-down-mint.svg");
  background-position: center;
  background-size: contain;
  background-repeat: no-repeat;

  transition: all 0.4s linear;
}

.faq.open .question {
  margin-bottom: 15px;
}

.faq.open .question::after {
  transform: translateY(-50%) rotate(180deg);
}

.faq .answer {
  color: #3c3c3c;
  font-size: 18px;
  opacity: 0;
  max-height: 0;
  overflow-y: hidden;
  transition: all 0.4s ease-out;
}

.faq.open .answer {
  opacity: 1;
  max-height: 100000px;
}
</style>
