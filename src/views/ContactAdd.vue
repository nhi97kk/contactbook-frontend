<template>
  <div class="page">
    <h4>Thêm mới Liên hệ</h4>
    <ContactForm :contact="newContact" @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    ContactForm,
  },
  // props: {
  //   id: { type: String, required: true },
  // },
  data() {
    return {
      // Tạo một đối tượng contact mới
      newContact: {
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
      message: "",
    };
  },
  methods: {
    async createContact(data) {
      try {
        await ContactService.create(data);
        this.message = "Liên hệ được thêm thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
