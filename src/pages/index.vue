<template>
  <div>
    <VCard
      class="mb-6"
      title="Kick start your project 🚀"
    >
      <VCardText>All the best for your new project.</VCardText>
      <VCardText>
        Please make sure to read our <a
          href="https://demos.pixinvent.com/vuexy-vuejs-admin-template/documentation/"
          target="_blank"
          rel="noopener noreferrer"
          class="text-decoration-none"
        >
          Template Documentation
        </a> to understand where to go from here and how to use our template.
      </VCardText>
    </VCard>

    <VCard title="Want to integrate JWT? 🔒">
      <VCardText>We carefully crafted JWT flow so you can implement JWT with ease and with minimum efforts.</VCardText>
      <VCardText>Please read our  JWT Documentation to get more out of JWT authentication.</VCardText>
    </VCard>
    <div>
    <h1>Google Sheets Data</h1>
    <pre>{{ sheetData }}</pre>
  </div>
  </div>
</template>
 
<script>
export default {
  data() {
    return {
      sheetData: [],
    };
  },
  created() {
    this.fetchSheetData();
  },
  methods: {
    fetchSheetData() {
      const sheetId = '1R459QAkvFyTYXb7P_Hs-Hxc2LNeAoK6K2_xZs1-jyz4';
      const apiKey = 'AIzaSyDhFVpHv6LWBbBlRCI_Lg0GeqMxvHWBiK8'; // Replace YOUR_ACTUAL_API_KEY with the API key you created
      const url = `https://sheets.googleapis.com/v4/spreadsheets/${sheetId}/values/A1:Z1000?key=${apiKey}`;
      
      fetch(url)
        .then(response => response.json())
        .then(data => {
          this.sheetData = data.values;
        })
        .catch(error => console.error('Error fetching Google Sheets data:', error));
    },
  },
};
</script>
