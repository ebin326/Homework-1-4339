<template>
    <!-- Vue template starts -->
    <form>
        <!-- Form for displaying facilities -->
        <h1>Facilities</h1>
        <!-- Heading for the form -->

        <ul>
            <!-- Unordered list to display facilities -->
            <li v-for="facility in facilities" v-on:click="toggleActive(facility)" v-bind:class="{ 'active': facility.active }">
                <!-- List item for each facility -->
                {{ facility.name }} <span>{{ formatCurrency(facility.price) }}</span>
                <!-- Display facility name and price -->
            </li>
        </ul>

        <div class="total">
            <!-- Div for displaying total -->
            Total: <span>{{ formatCurrency(total()) }}</span>
            <!-- Display total amount -->
        </div>
    </form>
</template>

<script>
export default {
    // Exporting Vue component
    data() {
        // Data function to return initial data
        return {
            facilities: [
                // Array of facilities
                {
                    name: 'Ballroom',
                    price: 5000,
                    active: true
                },
                {
                    name: 'Backyard',
                    price: 400,
                    active: false
                },
                {
                    name: 'Wellness Area',
                    price: 250,
                    active: false
                },
                {
                    name: 'Restaurant',
                    price: 220,
                    active: false
                }
            ]
        }
    },
    methods: {
        // Methods section for defining component methods
        toggleActive: function(s) {
            // Method to toggle facility's active state
            s.active = !s.active;
        },
        total: function() {
            // Method to calculate total amount
            var total = 0;
            this.facilities.forEach(function(facility) {
                if (facility.active) {
                    total += facility.price;
                }
            });
            return total;
        },
        formatCurrency(value) {
            // Method to format currency
            return '$' + value.toFixed(2);
        }
    }
}
</script>

<style scoped>
  /* Scoped CSS styles */
  form {
    /* Styling for the form */
    background-color: #8931EF;
    border-radius: 2px;
    box-shadow: 0 1px 1px #ccc;
    width: 400px;
    padding: 35px 60px;
    margin: 50px auto;
  }

  h1 {
    /* Styling for heading */
    color: #fff;
    font-size: 64px;
    font-family: 'Cookie', cursive;
    font-weight: normal;
    line-height: 1;
    text-shadow: 0 3px 0 rgba(0, 0, 0, 0.1);
  }

  ul {
    /* Styling for unordered list */
    list-style: none;
    color: #fff;
    font-size: 20px;
    font-weight: bold;
    text-align: left;
    margin: 20px 0 15px;
  }

  li {
    /* Styling for list item */
    padding: 20px 30px;
    background-color: #a5949a;
    margin-bottom: 8px;
    box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
    cursor: pointer;
  }

  li.active {
    /* Styling for active list item */
    background-color: #87E911;
  }

  .total {
    /* Styling for total */
    border-top: 1px solid rgba(255, 255, 255, 0.5);
    padding: 15px 30px;
    font-size: 20px;
    font-weight: bold;
    text-align: left;
    color: #fff;
  }

  .total span {
    /* Styling for total span */
    float: right;
  }
  </style>
