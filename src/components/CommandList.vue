<template>
  <div id="activityStackMain">
    <p v-if="activityStack.length == 0">
      <b>Anleitung</b>: Benutze das Chat-Fenster (Sprechblase unten rechts), um Anfragen in deutscher Sprache an die
      Datenbank zu
      stellen. Im großen Fenter erscheint dann ein Protokoll des Dialogs inklusive der dynamisch erzeugten
      SQL-Statements. Neue Einträge stehen oben auf der
      Seite.
    </p>
    <p v-if="activityStack.length > 0">Nachfolgend die dynamisch erzeugten SQL Statements:</p>
    <li v-for="(activityStackElement, index) in activityStack.slice().reverse()" :key="index"
      style="list-style-type: none">
      <p style="color: #212325; padding-top: 1.8em">
        <b>Eingabe</b>: „<i>{{ activityStackElement.nlRequest }}</i>”
      </p>

      <div v-for="(statement, index) in activityStackElement.sqlStatements" :key="index" style="list-style-type: none">
        <p style="
            color: #41b943;
            background-color: #010305;
            font-family: 'Courier New', Courier, monospace;
            margin-left: 0.7em;
            margin-top: 0.5em;
            margin-bottom: 0.5em;
            padding-top: 0.3em;
            padding-bottom: 0.3em;
          ">
          &nbsp;&nbsp;<b>{{ statement }}</b>
        </p>
      </div>

      <!--p style="color: coral; font-style: courier">{{ activityStackElement.sqlResponse }}</p-->
      <p style="color: #212325">
        <b>Antwort</b>: „<i>{{ activityStackElement.nlResponse }}</i>”
      </p>
    </li>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
// eslint-disable-next-line @typescript-eslint/no-var-requires
const emitter = require('tiny-emitter/instance');

type ActivityStackElement = {
  nlRequest: string;
  sqlStatements: string[];
  sqlResponse: string; // TODO
  nlResponse: string;
};

@Component({
  name: 'command-list',
})
export default class CommandList extends Vue {
  isVisible = false;

  activityStack: ActivityStackElement[] = [];

  async mounted() {
    console.log('mounted!');

    emitter.on(
      'add-new-query-event',
      (nlRequest: string, latestSqlStatements: string[], nlResponse: string) => {
        const newActivityStackElement: ActivityStackElement = {
          nlRequest: nlRequest,
          sqlStatements: latestSqlStatements,
          sqlResponse: 'some sql results ',
          nlResponse: nlResponse,
        };

        this.activityStack.push(newActivityStackElement);
      },
    );
  }
}
</script>

<style>
#activityStackMain {
  color: gra#414345;
  font-size: 1.3em;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
</style>
