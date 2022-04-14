<template>
  <div class="client-list">
    <p>Ordered by {{ order }}</p>
    <transition-group name="list" tag="ul">
      <li v-for="client in orderedClients" :key="client.id">
        <h2>
          {{ client.clientName }} - {{ client.location }} Branch in Zone
          {{ client.zone }}
        </h2>
        <div class="rate">
          <img src="@/assets/Cedi.svg" alt="cedi icon" />
          <p>{{ client.rate }} Ghana cedis</p>
        </div>
        <div class="service-type">
          <p>{{ client.serviceType }}</p>
        </div>
        <div class="survey-report">
          <p>{{ client.surveyReport }}</p>
        </div>
      </li>
    </transition-group>
  </div>
</template>
<script lang="ts">
import { computed, defineComponent, PropType } from "vue";
import Client from "@/types/Client";
import OrderTerm from "@/types/OrderTerm";

export default defineComponent({
  props: {
    clients: {
      required: true,
      type: Array as PropType<Client[]>,
    },
    order: {
      required: true,
      type: String as PropType<OrderTerm>,
    },
  },
  setup(props) {
    const orderedClients = computed(() => {
      return [...props.clients].sort((a: Client, b: Client) => {
        return a[props.order] > b[props.order] ? 1 : -1;
      });
    });
    return { orderedClients };
  },
});
</script>
<style scoped>
.client-list {
  max-width: 960px;
  margin: 40px auto;
}
.client-list ul {
  padding: 0;
}
.client-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
}
.client-list h2 {
  margin: 0 0 10px auto;
  text-transform: capitalize;
}
.rate {
  display: flex;
}
.rate img {
  margin-top: 12px;
  width: 20px;
  height: 15px;
}
.rate p {
  color: #16e2f5;
  font-weight: bold;
  margin: 10px 4px;
}
.list-move{
  transition: all 1s;
}
</style>
