<template>
  <div id="home">
    <nav class="text-sm font-semibold mb-6" aria-label="Breadcrumb">
      <ol class="list-none p-0 inline-flex">
        <li class="flex items-center text-red-500">
          <a href="#" class="text-gray-700">Home</a>
          <svg class="fill-current w-3 h-3 mx-3" viewBox="0 0 320 512">
            <path
              d="M285.476 272.971L91.132 467.314c-9.373 9.373-24.569 9.373-33.941 0l-22.667-22.667c-9.357-9.357-9.375-24.522-.04-33.901L188.505 256 34.484 101.255c-9.335-9.379-9.317-24.544.04-33.901l22.667-22.667c9.373-9.373 24.569-9.373 33.941 0L285.475 239.03c9.373 9.372 9.373 24.568.001 33.941z" />
          </svg>
        </li>
        <li class="flex items-center">
          <a href="#" class="text-gray-600">Dashboard</a>
        </li>
      </ol>
    </nav>

    <div class="lg:flex justify-between items-center mb-6">
      <p class="text-2xl font-semibold mb-2 lg:mb-0">Dashboard</p>
    </div>

    <div class="flex flex-wrap -mx-3 mb-20">

      <div class="w-1/2 xl:w-1/3 px-3">
        <div class="w-full bg-white border text-red-400 rounded-lg flex items-center p-6 mb-6 xl:mb-0">
          <svg class="w-16 h-16 fill-current mr-4 hidden lg:block" viewBox="0 0 20 20">
            <path
              d="M17.35,2.219h-5.934c-0.115,0-0.225,0.045-0.307,0.128l-8.762,8.762c-0.171,0.168-0.171,0.443,0,0.611l5.933,5.934c0.167,0.171,0.443,0.169,0.612,0l8.762-8.763c0.083-0.083,0.128-0.192,0.128-0.307V2.651C17.781,2.414,17.587,2.219,17.35,2.219M16.916,8.405l-8.332,8.332l-5.321-5.321l8.333-8.332h5.32V8.405z M13.891,4.367c-0.957,0-1.729,0.772-1.729,1.729c0,0.957,0.771,1.729,1.729,1.729s1.729-0.772,1.729-1.729C15.619,5.14,14.848,4.367,13.891,4.367 M14.502,6.708c-0.326,0.326-0.896,0.326-1.223,0c-0.338-0.342-0.338-0.882,0-1.224c0.342-0.337,0.881-0.337,1.223,0C14.84,5.826,14.84,6.366,14.502,6.708">
            </path>
          </svg>

          <div class="text-gray-700">
            <p class="font-semibold text-3xl">{{ sample_count }}</p>
            <p>Samples Tested</p>
          </div>

        </div>
      </div>
      <div class="w-1/2 xl:w-1/3 px-3">
        <div class="w-full bg-white border text-red-400 rounded-lg flex items-center p-6 mb-6 xl:mb-0">
          <div class="tooltip">
            <svg class="w-16 h-16 fill-current mr-4 hidden lg:block" v-on:click="case_negative += 1"
              viewBox="0 0 20 20">
              <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
              <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8z" />
            </svg>
            <span class="tooltiptext">Tooltip text</span>
          </div>
          <div class="text-gray-700">
            <p class="font-semibold text-3xl">{{ case_negative }}</p>
            <p>Negative Cases </p>
          </div>
        </div>
      </div>

      <div class="w-1/2 xl:w-1/3 px-3">
        <div class="w-full bg-white border text-red-400 rounded-lg flex items-center p-6">
          <svg class="w-16 h-16 fill-current mr-4 hidden lg:block" v-on:click="case_positive += 1" viewBox="0 0 20 20"
            id="positive_icon">
            <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
            <path
              d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z" />
          </svg>

          <div class="text-gray-700">
            <p class="font-semibold text-3xl">{{ case_positive }}</p>
            <p>Positive Cases</p>
          </div>
        </div>
      </div>

    </div>

    <div class="flex flex-wrap -mx-3">

      <div class="w-full xl:w-1/3 px-3">
        <p class="text-xl font-semibold mb-4">Recent Evaluations</p>

        <div class="w-full bg-white border rounded-lg p-4 mb-8 xl:mb-0">
          <canvas id="sample-chart" width="600" height="400"></canvas>
        </div>
      </div>

      <div class="w-full xl:w-1/3 px-3">
        <p class="text-xl font-semibold mb-4">Amount of samples (last week)</p>

        <div class="w-full bg-white border rounded-lg p-4 mb-8 xl:mb-0">
          <canvas id="sample-bar-chart" width="600" height="400"></canvas>
        </div>
      </div>

      <div class="w-full xl:w-1/3 px-3">
        <p class="text-xl font-semibold mb-4">Add Sample</p>

        <div class="w-full bg-white border rounded-lg p-4 mb-8 xl:mb-0">
          <button
            class="bg-gray-300 hover:bg-gray-400 text-red-800 font-bold py-2 px-4 my-2 rounded inline-flex items-center w-full"
            v-on:click="case_negative += 1">
            <svg class="fill-current mr-2 w-6 h-6 " viewBox="0 0 20 20">
              <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
              <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8z" />
            </svg>
            <span>Add negative case</span>
          </button>
          <button
            class="bg-gray-300 hover:bg-gray-400 text-red-800 font-bold py-2 px-4 rounded inline-flex items-center w-full"
            v-on:click="case_positive += 1">
            <svg class="fill-current w-6 h-6 mr-2" viewBox="0 0 20 20">
              <path d="M8 15A7 7 0 1 1 8 1a7 7 0 0 1 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z" />
              <path d="M4 8a.5.5 0 0 1 .5-.5h7a.5.5 0 0 1 0 1h-7A.5.5 0 0 1 4 8z" />
            </svg>
            <span>Add positive case</span>
          </button>
        </div>
      </div>

    </div>
  </div>

</template>

<script>
import Chart from 'chart.js'

export default {
  name: 'DashboardHome',
  data() {
    return {
      case_positive: 1,
      case_negative: 177,
      sampleData: {
        type: 'line',
        data: {
          labels: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          datasets: [{
            label: "Male",
            backgroundColor: "rgba(235, 91, 52,0.4)",
            strokeColor: "#63b3ed",
            pointColor: "#fff",
            pointStrokeColor: "#63b3ed",
            data: [203, 156, 99, 251, 305, 247, 256]
          },
          {
            label: "Female",
            backgroundColor: "rgba(235, 52, 104,0.4)",
            strokeColor: "#f7fafc",
            pointColor: "#fff",
            pointStrokeColor: "#f7fafc",
            data: [86, 97, 144, 114, 94, 108, 156]
          }]
        },
        options: {
          legend: {
            display: false
          },
          scales: {
            yAxes: [{
              gridLines: {
                display: false
              },
              ticks: {
                display: false
              }
            }],
            xAxes: [{
              gridLines: {
                display: false
              }
            }]
          }
        }
      },
      samplesTaken: {
        type: 'bar',
        data: {
          labels: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
          datasets: [{
            backgroundColor: "rgba(235, 91, 52,0.4)",
            strokeColor: "#63b3ed",
            pointColor: "#fff",
            pointStrokeColor: "#63b3ed",
            data: [203, 156, 99, 251, 305, 247, 256]
          }]
        },
        options: {
          legend: {
            display: false
          },
          scales: {
            yAxes: [{
              gridLines: {
                display: false
              },
              ticks: {
                display: false
              }
            }],
            xAxes: [{
              gridLines: {
                display: false
              }
            }]
          }
        }

      }
    }
  },
  mounted() {
    new Chart(document.getElementById('sample-chart'), this.sampleData)
    new Chart(document.getElementById('sample-bar-chart'), this.samplesTaken)
  },
  computed: {
    sample_count: function () {
      return this.case_negative + this.case_positive
    },

    increasePositive: function () {
      return this.case_positive + 1;
    }
  }
}
</script>

<style scoped>
.tooltip {
  position: relative;
  display: inline-block;
}

.tooltip .tooltiptext {
  visibility: hidden;
  width: 120px;
  background-color: black;
  color: #fff;
  text-align: center;
  padding: 5px 0;
  border-radius: 6px;
  position: absolute;
  z-index: 1;
}

.tooltip:hover .tooltiptext {
  visibility: visible;
}
</style>