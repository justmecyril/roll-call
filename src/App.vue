<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="@/assets/security-officer.svg" alt="">
        <h1>Tango Security Clientele</h1>
      </div>
      <div class="order">
        <button @click="handleClick('zone')">sort by zone</button>
        <button @click="handleClick('rate')">sort by rate</button>
        <button @click="handleClick('serviceType')">sort by service</button>
      </div>
    </header>

    <ClientList :clients="clients" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import ClientList from "@/components/ClientList.vue";
import Client from "@/types/Client";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  name: "App",
  components: { ClientList },
  setup() {
    const clients = ref<Client[]>([
      {
        clientName: "CBG",
        location: "Airport",
        rate: 1500,
        zone: "B",
        contact: 233222222222,
        serviceType: "Day & Night",
        surveyReport: "5 day guards and 3 night guards",
        id: "1",
      },
      {
        clientName: "ADB",
        location: "Ridge",
        rate: 2600,
        zone: "A",
        contact: 233333333333,
        serviceType: "Day",
        surveyReport: "5 day guards",
        id: "3",
      },
      {
        clientName: "UBA",
        location: "Accra",
        rate: 4700,
        zone: "D",
        contact: 233444444444,
        serviceType: "Day & Night",
        surveyReport: "3 day guards and 3 night guards",
        id: "4",
      },
      {
        clientName: "ABSA",
        location: "Ridge",
        rate: 5800,
        zone: "C",
        contact: 233555555555,
        serviceType: "Night",
        surveyReport: "2 day guards and 3 night guards",
        id: "2",
      },
      {
        clientName: "ACCESS",
        location: "Osu",
        rate: 3900,
        zone: "E",
        contact: 233666666666,
        serviceType: "Day & Night",
        surveyReport: "4 day guards and 2 night guards",
        id: "5",
      },
    ]);

    const order = ref<OrderTerm>("clientName");

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { clients, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #16e2f5;
  background: #ffffff;
  padding: 8px 16px;
  border-radius: 12px;
  cursor: pointer;
  font-weight: bold;
}
header .title{
  display: flex;
  justify-content: center;
}
header img{
  width: 60px;
  margin-right: 20px;
}
header h1{
  font-size: 3em;
}
</style>
