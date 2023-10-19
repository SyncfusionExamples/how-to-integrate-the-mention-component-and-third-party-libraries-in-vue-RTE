<script>
import { RichTextEditorComponent, Toolbar, Image, HtmlEditor, Link, Table, QuickToolbar } from '@syncfusion/ej2-vue-richtexteditor';
import { MentionComponent } from '@syncfusion/ej2-vue-dropdowns';

export default {
  name: "App",
  components: {
    "ejs-richtexteditor": RichTextEditorComponent,
    "ejs-mention" : MentionComponent
  },
  data : function()
  {
    return{
      data: {
        userData: [ 'Selma Rose', 'Garth', 'Robert', 'William', 'Joseph']
      }
    }
  },
  methods : {
    actionCompleteHandler : function (args) {
      if(args.requestType === 'Links')
      {
        const embedCardElement = document.createElement('blockquote');
        embedCardElement.setAttribute('class', 'embedly-card');
        embedCardElement.appendChild(args.elements[0].parentElement);
        embedCardElement.appendChild(document.createElement('p'));
        args.range.insertNode(embedCardElement);
      }
    }
  },
  provide: {
    richtexteditor: [Toolbar, Image, HtmlEditor, Link, Table, QuickToolbar]
  }
}

</script>
<template>
  <ejs-richtexteditor id="mention_integration" placeholder="Type @ and tag the name" width="900px" height="300px"
                      :actionComplete="actionCompleteHandler">
  </ejs-richtexteditor>
  <ejs-mention target="#mention_integration_rte-edit-view" :dataSource = ' data.userData '></ejs-mention>
</template>

<style>
@import "../node_modules/@syncfusion/ej2-base/styles/material.css";
@import "../node_modules/@syncfusion/ej2-inputs/styles/material.css";
@import "../node_modules/@syncfusion/ej2-lists/styles/material.css";
@import "../node_modules/@syncfusion/ej2-popups/styles/material.css";
@import "../node_modules/@syncfusion/ej2-buttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-navigations/styles/material.css";
@import "../node_modules/@syncfusion/ej2-splitbuttons/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-richtexteditor/styles/material.css";
@import "../node_modules/@syncfusion/ej2-vue-dropdowns/styles/bootstrap5.css";
</style>