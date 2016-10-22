<template>
  <div id="app">
    <header>
      <address>
        <p class="title">{{ identity.name }}</p>
        <ul>
          <li><i class="fa fa-birthday-cake"></i>{{ birthday|date }} ({{ age }} ans)</li>
          <li><i class="fa fa-map-marker"></i><span v-html="identity.address"></span></li>
          <li><i class="fa fa-phone"></i><a href="tel:0629017973">{{ identity.phone }}</a></li>
          <li><i class="fa fa-envelope"></i><a href="mailto:corentihembise@free.fr">{{ identity.mail }}</a></li>
        </ul>
      </address>
      <img :src="identity.image">
    </header>
    <div class="cb"></div>
    <main>
      <timeline title="Expériences professionnelles" :items="professionals"></timeline>
      <timeline title="Formation" :items="formations"></timeline>
      <article class="sub-hier">
        <h1>Compétences</h1>
        <h2>Langues</h2>
        <dl>
          <dt>Anglais</dt>
          <dd>Niveau moyen</dd>
          </br>
          <dt>Espagnol</dt>
          <dd>Bonnes notions</dd>
        </dl>
        <h2>Informatiques</h2>
        <h2>Centres d'intérêt</h2>
        <p>Projets électronique (carte arduino, raspberry)</br>
        Projets d’applications web</br></p>
      </article>
    </main>
  </div>
</template>

<script>
import Timeline from './Timeline.vue'

export default {
  name: 'app',
  components: { Timeline },
  filters: {
    date : function(value) {
      return value.getDate() + '/' + (parseInt(value.getMonth())+1) + '/' + value.getFullYear();
    }
  },
  computed: {
      age : function() {
        var ageDifMs = Date.now() - this.birthday.getTime();
        var ageDate = new Date(ageDifMs); // miliseconds from epoch
        return Math.abs(ageDate.getUTCFullYear() - 1970);
      },
      birthday: function() {
        return new Date(this.identity.birthday)
      }
  },
  data () {
    return {
      identity : {
        image: 'src/assets/photoCV.jpg',
        name: 'HEMBISE Corentin',
        birthday: "12/12/1996",
        address: "175 rue du Paradis</br>60400 CAISNES",
        phone: '06 29 01 79 73',
        mail: 'corentihembise@free.fr'
      },
      professionals : [
        {
          start: 'oct. 2015',
          end  : 'maintenant',
          title: 'Développeur en apprentissage',
          subtitle: 'Biper Studio, PARIS 11 ème',
          description: 'Développement sous Symfony2 en équipe.'
        },
        {
          start: 'juil. 2015',
          end  : 'sept.2015',
          title: 'Développeur / Webdesigner',
          subtitle: 'Ebip, NOYON (60)',
          description: "Conception et développement d'un site vitrine et de l’identité graphique pour une société d’électricité."
        },
        {
          start: 'dec. 2010',
          title: 'Stage d’observation en 3<sup>ème</sup>',
          subtitle: 'MicroMusic, NOYON (60)',
          description: "Assemblage d'ordinateur, vente de composants/ordinateurs, réparation informatique."
        }
      ],
      formations : [
        {
          start: '2014',
          end: 'maintenant',
          title: 'Université de Valenciennes et du Hainaut Cambrésis, </br>IUT MAUBEUGE (59)',
          subtitle: 'DUT Informatique',
        },
        {
          start: '2011',
          end: '2014',
          title: 'Lycée Jean Calvin, NOYON (60)',
          subtitle: 'BAC Scientifique science de l’ingénieur (Option informatique), mention bien',
        }
      ]
    }
  }
}
</script>

<style>
body {
  font-family: Open Sans;
  font-weight: lighter;
  font-size: 16px;
  margin: 4rem;
  color: #353535;
}

h1, h2, h3, h4 {
  font-weight: normal;
}

a {
  color: inherit;
  text-decoration: none;
}

header {
}

header img {
  width: 127px;
  float: right;
}

.cb {
  clear: both;
}

header address {
  font-style: normal;
  float: left;
}
header address .title {
  font-weight: normal;
  font-size: 1.95rem;
  margin-top: 0;
  margin-bottom: .8rem;
}
header address ul {
  list-style: none;
  padding-left: 0;
  padding-left: 22px;
  color: #777777;
}
header address ul li {
  position: relative;
  margin-bottom: 3px;
}
header address ul li i {
  position: absolute;
  top: 2px;
  left: -22px;
}

main article h1 {
  font-variant: petite-caps;
  font-size: 2rem;
  position: relative;
  color: #515254;
}

main article h1::after {
  content: '';
  position: absolute;
  height: 4px;
  width: 50%;
  background: #EDEDED;
  top:50%;
  right: 0;
  border-radius: 10px;
  transform: translateY(-50%);
  margin-right: -4rem;
}

main article ul.timeline {
  position: relative;
  padding-left: 11rem;
}

main article ul.timeline li {
  list-style: none;
  position: relative;
  margin-left: 2rem;
  margin-bottom: 1rem;
}
main article ul.timeline li::before {
  content: '';
  position: absolute;
  height: 8px;
  width: 8px;
  border: 4px solid #50c063;
  border-radius: 50%;
  background: #FFF;
  left: -37px;
  top: 6px;
}
main article ul.timeline li span {
  position: absolute;
  left: -13.5rem;
  text-align: right;
  width: 10rem;
  line-height: 1.6rem;
  font-size: .9rem;
}
main article ul.timeline li h2 {
  font-size: 1.3rem;
  margin: 0;
}
main article ul.timeline li h3 {
  font-weight: lighter;
  margin: 0;
  color: #8d8e90;
}
main article ul.timeline li p {
  margin-top: .3rem;
  margin-bottom: 0;
  margin-left: 1rem;
  font-weight: normal;
  color: #8d8e90;
}
main article ul.timeline::before {
  position: absolute;
  content: '';
  height: 95%;
  width: 6px;
  top: 6px;
  border-radius: 6px;
  background: #50c063;
}

main article.sub-hier h2 {
  font-size: 1.3rem;
  width: 11rem;
  text-align: right;
  color: #848484;
  margin-bottom: 0;
}
main article.sub-hier dl {
  margin: 0;
}
main article.sub-hier dl dt {
  width: 11rem;
  text-align: right;
  color: #8d8e90;
  display: inline-block;
}
main article.sub-hier dl dd {
  display: inline-block;
  margin-left: 1.5rem;
}
main article.sub-hier p {
  margin-left: 11rem;
  padding-left: 1rem;
}
</style>
