<template>
  <section id="timeline" class="py-16">
    <v-container>
      <h2 class="text-h3 text-center font-weight-black mb-8">Our Journey</h2>
      <template>
        <v-timeline>
          <v-timeline-item
            v-for="(year, i) in years"
            :key="i"
            :color="year.color"
            small
          >
            <template v-slot:opposite>
              <span
                :class="`headline font-weight-bold ${year.color}--text`"
                v-text="year.year"
              ></span>
              <h2
                :class="`headline font-weight-light mb-4 ${year.color}--text`"
              >
                Founded
              </h2>
            </template>
            <div class="py-4">
              <h2
                :class="`headline font-weight-light mb-4 ${year.color}--text`"
              >
                Founded
              </h2>
              <div>
                Achievement Text
              </div>
            </div>
          </v-timeline-item>
        </v-timeline>
      </template>
    </v-container>
  </section>
</template>

<script>
export default {
  data() {
    return {
      years: [
        {
          color: 'cyan',
          year: '2019',
        },
        {
          color: 'green',
          year: '2020',
        },
        {
          color: 'pink',
          year: '2021',
        },
        {
          color: 'amber',
          year: '2022',
        },
        {
          color: 'orange',
          year: '2023',
        }
      ],
    }
  },
}
</script>
