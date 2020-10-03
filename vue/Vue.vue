new Vue({
  el: '#App',
  data: {
    sortKey: 'name',
    reverse: false,
    search: '',
    Products: [
      { name: 'Двери' },
      { name: 'Пиломатериалы' },
      { name: 'Лестницы' },
      { name: 'Окна, стекло' },
      { name: 'Потолки' },
      { name: 'Плитка и камни' },
      { name: 'Мебель' },
    ],
  },
  computed: {
    sortedUsers() {
      const k = this.sortKey;
      return this.Products.sort((a, b) => {
        return (a[k] < b[k] ? -1 : a[k] > b[k] ? 1 : 0) * [ 1, -1 ][+this.reverse];
      });
    },
    filteredUsers() {
      const s = this.search.toLowerCase();
      return this.sortedUsers.filter(n => {
        return Object.values(n).some(m => m.toString().toLowerCase().includes(s));
      });
    },
  }
});
