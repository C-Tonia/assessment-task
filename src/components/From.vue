<script setup>
import { ref } from "vue";
import axios from "axios";

const options = ["HP", "DELL", "ACER", "MACBOOK"];
const inputField = ref({
  fullName: "",
  phone: "",
  email: "",
  address: "",
  laptop: "",
  receipt: "",
});

function onFileChange(e) {
  inputField.value.receipt = e.target.files || e.dataTransfer.files;
  console.log(inputField.value.receipt);
}
function sendData() {
  axios
    .post(
      "https://testbackend-ya01.onrender.com/api/v1/openapi.json",

      JSON.stringify({
        fullname: inputField.value.fullName,
        phone: inputField.value.phone,
        email: inputField.value.email,
        address: inputField.value.address,
        laptop: inputField.value.laptop,
        receipt: inputField.value.receipt.files,
      })
    )
    .then((response) => console.log(response, "hello"));

  inputField.value.address = "";
  inputField.value.email = "";
  inputField.value.fullName = "";
  inputField.value.receipt = "";
  inputField.value.laptop = "";
  inputField.value.phone = "";
}
</script>
<template>
  <form class="font-inter w-96" @submit.prevent="sendData">
    <div class="form-group mt-2">
      <label for="full-name" class="block font-medium">Full name</label>
      <input
        type="text"
        class="w-full py-2 px-3 outline-none border-0 rounded-lg"
        v-model="inputField.fullName"
        placeholder="John Doe"
      />
    </div>
    <div class="form-group mt-2">
      <label for="phone-number" class="block font-medium">Phone Number</label>
      <input
        type="tel"
        v-model="inputField.phone"
        class="w-full py-2 px-3 outline-none border-0 rounded-lg"
        placeholder="+234000000000"
      />
    </div>
    <div class="form-group mt-2">
      <label for="email" class="block font-medium">Email</label>
      <input
        v-model="inputField.email"
        type="email"
        class="w-full py-2 px-3 outline-none border-0 rounded-lg"
        placeholder="mailat@example.com"
      />
    </div>
    <div class="form-group mt-2">
      <label for="text" class="block font-medium">Address</label>
      <input
        v-model="inputField.address"
        type="type"
        class="w-full py-2 px-3 outline-none border-0 rounded-lg"
        placeholder="38 Crescent Avenue"
      />
    </div>
    <div class="form-group mt-2">
      <label for="spec" class="block font-medium">Laptop Specification </label>
      <select
        name="Laptop spec"
        id="spec"
        class="w-full py-2 px-3 outline-none border-0 rounded-lg border-0 outline-none"
        v-model="inputField.laptop"
      >
        <option value="" disabled selected hidden class="text-gray-300">
          Select Laptop Type
        </option>
        <option :value="option" v-for="option in options">{{ option }}</option>
      </select>
    </div>
    <div class="form-group mt-2">
      <label for="upload" class="block font-medium cursor-pointer"
        >Upload receipt of old laptop
        <br />
        <span class="rounded-lg inline-block bg-white px-6 py-1">
          <i class="ri-upload-cloud-2-line text-2xl text-gray-400"></i>
        </span>
        <input type="file" id="upload" class="hidden" @change="onFileChange" />
      </label>
    </div>
    <div class="form-group mt-4">
      <button class="bg-[#335CA6] text-white py-2 px-5 rounded-lg">
        Submit
      </button>
    </div>
  </form>
</template>
