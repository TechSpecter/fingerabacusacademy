<template>
  <section>
    <v-row no-gutters>
      <v-col cols="12">
        <SectionsHeroAlt :hero-alt="heroAlt" />
        <SectionsTeam :our-team="ourTeam" />

        <v-row no-gutters>
          <v-col cols="12" md="6" align-self="center">
            <v-img max-height="800" src="pexels-canva-studio-3277806.jpg" lazy-src="pexels-canva-studio-3277806.jpg">
            </v-img>
          </v-col>
          <v-col cols="12" md="6" align-self="center">
            <div class="pa-lg-16 pa-md-10 px-4 py-16">
              <h2 class="text-h3 text-center font-weight-black">Our Vision</h2>
              <h3 class="text-h5 font-weight-thin text-center my-8">
                Fostering a future where mathematical mastery is accessible to all through the timeless art of Finger Abacus, empowering individuals to excel academically and tackle real-world challenges with confidence.
              </h3>
              <p>
                At Finger Abacus Academy, our vision is to revolutionize mathematics education by harnessing the power of
                Finger Abacus techniques. We envision a future where every student, regardless of their mathematical
                background, can confidently embrace the beauty of numbers and master mental math.<br><br>
                Our commitment to innovation drives us to continuously explore and integrate modern teaching methods with
                this age-old technique, making it accessible and engaging for learners of all ages. We aspire to create a
                global community of math enthusiasts who not only excel academically but also approach real-world
                challenges with precision, creativity, and confidence. <br><br>
                Join us on this exciting journey as we redefine the way mathematics is learned and embraced, and as we
                empower individuals to unlock their full mathematical potential.
              </p>
            </div>
          </v-col>
        </v-row>
        <v-row no-gutters class="flex-row-reverse">
          <v-col cols="12" md="6" align-self="center">
            <v-img max-height="800" src="pexels-rfstudio-3810792.jpg" lazy-src="pexels-rfstudio-3810792.jpg">
            </v-img>
          </v-col>
          <v-col cols="12" md="6" align-self="center">
            <div class="pa-lg-16 pa-md-10 px-4 py-16">
              <h2 class="text-h3 text-center font-weight-black">Our Mission</h2>
              <h3 class="text-h5 font-weight-thin text-center my-8">
                Cultivating mathematical excellence through the art of Finger Abacus. Our mission is to empower students
                with this ancient technique, fostering not only mathematical proficiency but also mental acuity,
                creativity, and self-confidence. At Finger Abacus Academy, we're shaping future problem solvers and
                critical thinkers.
              </h3>
              <p>
                <b>Empowerment</b>: The academy's mission is to empower students, indicating a focus on enhancing their
                abilities
                and self-confidence.<br>
                <b>Ancient Art</b>: Mentioning the "ancient art of Finger Abacus" highlights the unique and time-tested
                nature of
                the education provided.<br>
                <b>Holistic Development</b>: The mission goes beyond just teaching math skills and emphasizes the
                development of
                cognitive and soft skills, such as critical thinking and problem-solving. <br>
                <b>Innovation</b>: It highlights the academy's commitment to modern and innovative teaching methods. <br>
                <b>Limitless Possibilities</b>: The mission statement suggests that the academy's education equips
                students to
                excel in various aspects of life, not just academics.
              </p>
            </div>
          </v-col>
        </v-row>

        <SectionsTimeline />
      </v-col>
    </v-row>
  </section>
</template>

<script>
export default {
  data() {
    return {
      heroAlt: [
        {
          src: 'pexels-moose-photos-1036641.jpg',
          heading: 'About Us',
        },
      ],
      ourTeam: [
        {
          name: 'Deepti Gupta',
          position: 'Founder and Tutor',
          phone: '+91 (987) 1625346',
          email: 'deepti@example.com',
          photo: 'person-2.jpg',
        },
        {
          name: 'Deepak Gupta',
          position: 'Manager',
          phone: '+91 (987) 6982456',
          email: 'deepak@example.com',
          photo: 'person-1.jpg',
        },
      ]
    }
  },
  head() {
    return {
      title: 'About Us',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            "Learn about FingerAbacus Academy's mission to empower students with mental math skills, experienced instructors, and a commitment to holistic learning. Discover why we're the choice for mathematical success.",
        },
      ],
    }
  },
}
</script>
