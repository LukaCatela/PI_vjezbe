<script setup>
      const slike = {
        "Jabuka": "https://www.svgrepo.com/show/530203/apple.svg",
        "Mrkva": "https://www.svgrepo.com/show/530216/carrot.svg",
        "Sir": "https://www.svgrepo.com/show/530219/cake.svg",
        "Kruh": "https://www.svgrepo.com/show/530223/bread.svg",
        };
      const proizvodi = [
          { naziv: "Jabuka", cijena: 0.25 },
          { naziv: "Mrkva", cijena: 0.12 },
          { naziv: "Kruh", cijena: 2.00 },
          { naziv: "Sir", cijena: 4.48 }
          ];
      const korisnik = {
          jeAdmin: true,
          osobni_podaci: {
          ime: "Marko",
          prezime: "Krivić",
          adresa: {
          grad: "Pula",
          ulica: "Veruda",
          broj: 32
          },
        broj_telefona: "+091-123-456"
        },
        kosarica :[
        { naziv: "Jabuka", količina: 4 },
        { naziv: "Mrkva", količina: 12 },
        { naziv: "Sir", količina: 1 },
        { naziv: "Kruh", količina: 3 },
        ]
      }  

</script>

<template>
  <div class="box-border">{{ kosarica }}</div>
  
</template>

<style scoped>

</style>
