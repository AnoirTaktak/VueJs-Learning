<template>
    <div>
    <Entetefacture :fact="facture"/>
    <Detailfacture :articles="articles" 
    :deletearticle="deletearticle"
    :updatearticle="updatearticle"/>
    <Formfacture :ajoutLigne="ajoutLigne"/>
    </div>
    </template>
    <script setup>

    import { ref } from "vue";
    import Entetefacture from "./Entetefacture.vue";
    import Formfacture from "./Formfacture.vue";
    import Detailfacture from "./Detailfacture.vue";

    const facture =ref({
        numfact:"100",
        datefact:"18/05/2022",
        raisoc:"Confort-Plus",
        responsable:"Turki Mounir"
    });

    const articles=ref([
        {reference:"1",designation:"lavaisselle",qte:3,prix:1500},
        {reference:"3",designation:"Machine alaver",qte:3,prix:1200},
        {reference:"17",designation:"Micro-onde",qte:4,prix:300}
    ]);

    const ajoutLigne =(ref,des,qt,pr)=>{
        let ligne={reference:ref,designation:des,qte:qt,prix:pr}
        articles.value.push(ligne)
    }


    const deletearticle = (reference) => {
        articles.value=articles.value.filter((article) => article.reference !==
        reference);
    };


    const updatearticle = (articlemodif) => {
        console.log("article est",articlemodif.reference)
        articles.value=articles.value.map((article) =>
        article.reference === articlemodif.reference ? articlemodif : article
        )
    }
</script>
<style lang="scss" scoped>
</style>