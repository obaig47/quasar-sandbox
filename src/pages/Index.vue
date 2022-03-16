<template>
  <q-page padding>
    <!-- This is javascript inside of the quotes-->
    <!--For message when hovering over something @mouseenter="alertMessage" -->
    <input
      v-model="message"
      @keyup.esc="clearMessage"
      @keyup.enter="alertMessage"
    />
    <button @click="clearMessage">Clear</button>
    <!-- In this instance, this is being hidden with CSS styles-->
    <!-- <h5 class="border-grey" v-show="message.length">{{ message }}</h5> -->
    <h5 class="border-grey" v-if="message.length">{{ message }}</h5>
    <h6 v-else>No message entered</h6>

    <hr />
    <p></p>

    <!-- CARD CONTAINER -->
    <div class="q-pa-md row items-start q-gutter-md">
      <!-- CARD START -->
      <q-card class="my-card" flat bordered>
        <!--<q-img src="https://cdn.quasar.dev/img/parallax2.jpg"></q-img>-->

        <div class="col-auto">
          <q-btn color="grey-7" round flat icon="more_vert">
            <q-menu cover auto-close>
              <q-list>
                <q-item>
                  <q-item-section
                    >Lorem ipsum dolor sit amet, consectetur adipiscing elit,
                    sed do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua.</q-item-section
                  >
                </q-item>
                <q-item clickable>
                  <q-item-section>Send Feedback</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Share</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
        </div>

        <q-card-section>
          <div class="text-overline text-orange-9">Overline</div>
          <div class="text-h5 q-mt-sm q-mb-xs">Title</div>
          <div class="text-caption text-grey">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </div>
        </q-card-section>

        <q-card-actions>
          <q-space></q-space>
          <!-- DROPDOWN BUTTON -->
          <q-btn
            color="grey"
            round
            flat
            dense
            :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
            @click="expanded = !expanded"
          ></q-btn>
        </q-card-actions>

        <q-slide-transition>
          <div v-show="expanded">
            <q-separator></q-separator>
            <q-card-section class="text-subitle2">
              {{ stats }}
            </q-card-section>
          </div>
        </q-slide-transition>

        <!-- BEGIN INBOX LIST -->
        <q-list bordered class="rounded-borders">
          <q-expansion-item
            expand-separator
            icon="mail"
            label="Inbox"
            caption="5 unread emails"
            default-opened
          >
            <q-expansion-item
              :header-inset-level="1"
              expand-separator
              icon="receipt"
              label="Receipts"
              default-opened
            >
              <q-expansion-item
                switch-toggle-side
                dense-toggle
                label="Today"
                :header-inset-level="1"
                :content-inset-level="2"
              >
                <q-card>
                  <q-card-section>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                    Quidem, eius reprehenderit eos corrupti commodi magni
                    quaerat ex numquam, dolorum officiis modi facere maiores
                    architecto suscipit iste eveniet doloribus ullam aliquid.
                  </q-card-section>
                </q-card>
              </q-expansion-item>

              <q-expansion-item
                switch-toggle-side
                dense-toggle
                label="Yesterday"
                :header-inset-level="1"
                :content-inset-level="2"
              >
                <q-card>
                  <q-card-section>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                    Quidem, eius reprehenderit eos corrupti commodi magni
                    quaerat ex numquam, dolorum officiis modi facere maiores
                    architecto suscipit iste eveniet doloribus ullam aliquid.
                  </q-card-section>
                </q-card>
              </q-expansion-item>
            </q-expansion-item>

            <q-expansion-item
              :header-inset-level="1"
              :content-inset-level="1"
              expand-separator
              icon="schedule"
              label="Postponed"
            >
              <q-card>
                <q-card-section>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                  Quidem, eius reprehenderit eos corrupti commodi magni quaerat
                  ex numquam, dolorum officiis modi facere maiores architecto
                  suscipit iste eveniet doloribus ullam aliquid.
                </q-card-section>
              </q-card>
            </q-expansion-item>
          </q-expansion-item>

          <q-expansion-item
            :content-inset-level="0.5"
            expand-separator
            icon="mail"
            label="Inbox"
            caption="5 unread emails"
            default-opened
          >
            <q-expansion-item
              expand-separator
              :content-inset-level="0.5"
              icon="receipt"
              label="Receipts"
            >
              <q-expansion-item label="Today" :content-inset-level="0.5">
                <q-card>
                  <q-card-section>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                    Quidem, eius reprehenderit eos corrupti commodi magni
                    quaerat ex numquam, dolorum officiis modi facere maiores
                    architecto suscipit iste eveniet doloribus ullam aliquid.
                  </q-card-section>
                </q-card>
              </q-expansion-item>

              <q-expansion-item label="Yesterday" :content-inset-level="0.5">
                <q-card>
                  <q-card-section>
                    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                    Quidem, eius reprehenderit eos corrupti commodi magni
                    quaerat ex numquam, dolorum officiis modi facere maiores
                    architecto suscipit iste eveniet doloribus ullam aliquid.
                  </q-card-section>
                </q-card>
              </q-expansion-item>
            </q-expansion-item>

            <q-expansion-item
              :content-inset-level="0.5"
              expand-separator
              icon="schedule"
              label="Postponed"
            >
              <q-card>
                <q-card-section>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit.
                  Quidem, eius reprehenderit eos corrupti commodi magni quaerat
                  ex numquam, dolorum officiis modi facere maiores architecto
                  suscipit iste eveniet doloribus ullam aliquid.
                </q-card-section>
              </q-card>
            </q-expansion-item>
          </q-expansion-item>
        </q-list>
        <!-- END INBOX LIST -->

        <!-- BEGIN INFO BUTTON TO DIALOG -->
        <q-btn label="Alert" color="primary" @click="alert = true" />
        <q-dialog v-model="alert">
          <q-card>
            <q-card-section>
              <div class="text-h6">Alert</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
              repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
              perferendis totam, ea at omnis vel numquam exercitationem aut,
              natus minima, porro labore.
            </q-card-section>

            <q-card-actions align="right">
              <q-btn flat label="OK" color="primary" v-close-popup />
            </q-card-actions>
          </q-card>
        </q-dialog>
        <!-- END INFO BUTTON TO DIALOG -->
      </q-card>

      <!-- SECOND CARD START -->

      <!-- CARD START -->
      <q-card class="my-card" flat bordered>
        <!--<q-img src="https://cdn.quasar.dev/img/parallax2.jpg"></q-img>-->

        <div class="col-auto">
          <q-btn color="grey-7" round flat icon="more_vert">
            <q-menu cover auto-close>
              <q-list>
                <q-item>
                  <q-item-section
                    >Lorem ipsum dolor sit amet, consectetur adipiscing elit,
                    sed do eiusmod tempor incididunt ut labore et dolore magna
                    aliqua.</q-item-section
                  >
                </q-item>
                <q-item clickable>
                  <q-item-section>Send Feedback</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>Share</q-item-section>
                </q-item>
              </q-list>
            </q-menu>
          </q-btn>
        </div>

        <q-card-section>
          <div class="text-overline text-orange-9">Accounts Accessed</div>
          <div class="text-h5 q-mt-sm q-mb-xs">Title</div>
          <div class="text-caption text-grey">
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
            eiusmod tempor incididunt ut labore et dolore magna aliqua.
          </div>
        </q-card-section>

        <q-card-actions>
          <q-space></q-space>
          <!-- DROPDOWN BUTTON -->
          <q-btn
            color="grey"
            round
            flat
            dense
            :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
            @click="expanded = !expanded"
          ></q-btn>
        </q-card-actions>

        <q-slide-transition>
          <div v-show="expanded">
            <q-separator></q-separator>

            <div class="row">
              <div class="col q-pa-sm">
                Hello
                <q-separator></q-separator>
                <a href="">Website 1<q-icon name="open_in_new"></q-icon></a>
              </div>
              <div class="col q-pa-sm">
                Hello
                <q-separator></q-separator>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt ut labore et dolore magna aliqua.
              </div>
            </div>
          </div>
        </q-slide-transition>

        <!-- BEGIN INFO BUTTON TO DIALOG -->
        <q-btn label="Alert" color="primary" @click="alert = true" />
        <q-dialog v-model="alert">
          <q-card>
            <q-card-section>
              <div class="text-h6">Alert</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
              repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
              perferendis totam, ea at omnis vel numquam exercitationem aut,
              natus minima, porro labore.
            </q-card-section>

            <q-card-actions align="right">
              <q-btn flat label="OK" color="primary" v-close-popup />
            </q-card-actions>
          </q-card>
        </q-dialog>
        <!-- END INFO BUTTON TO DIALOG -->
      </q-card>
      <!-- END CARD 2 -->
    </div>
    <!-- CARD CONTAINER -->

    <q-markup-table :separator="separator" flat bordered>
      <thead>
        <tr>
          <th class="text-left">Dessert (100g serving)</th>
          <th class="text-right">Calories</th>
          <th class="text-right">Fat (g)</th>
          <th class="text-right">Carbs (g)</th>
          <th class="text-right">Protein (g)</th>
          <th class="text-right">Sodium (mg)</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="text-left">Frozen Yogurt</td>
          <td class="text-right">159</td>
          <td class="text-right">6</td>
          <td class="text-right">24</td>
          <td class="text-right">4</td>
          <td class="text-right">87</td>
        </tr>
        <tr>
          <td class="text-left">Ice cream sandwich</td>
          <td class="text-right">237</td>
          <td class="text-right">9</td>
          <td class="text-right">37</td>
          <td class="text-right">4.3</td>
          <td class="text-right">129</td>
        </tr>
        <tr>
          <td class="text-left">Eclair</td>
          <td class="text-right">262</td>
          <td class="text-right">16</td>
          <td class="text-right">23</td>
          <td class="text-right">6</td>
          <td class="text-right">337</td>
        </tr>
        <tr>
          <td class="text-left">Cupcake</td>
          <td class="text-right">305</td>
          <td class="text-right">3.7</td>
          <td class="text-right">67</td>
          <td class="text-right">4.3</td>
          <td class="text-right">413</td>
        </tr>
        <tr>
          <td class="text-left">Gingerbread</td>
          <td class="text-right">356</td>
          <td class="text-right">16</td>
          <td class="text-right">49</td>
          <td class="text-right">3.9</td>
          <td class="text-right">327</td>
        </tr>
      </tbody>
    </q-markup-table>
  </q-page>
</template>

<script>
// This is a required line in Vue 3
import { defineComponent } from "vue";
import { ref } from "vue";

export default defineComponent({
  props: {
    increase: {
      type: Boolean,
      required: false,
      default: true,
    },
  },
  data() {
    return {
      message: "I love Vue.js",
      expanded: ref(false),
      alert: ref(false),
      stats: 23123123,
    };
  },
  methods: {
    clearMessage() {
      this.message = "";
    },
    alertMessage() {
      alert(this.message);
    },
  },
});
</script>

<style lang="sass" scoped>
.border-grey
  border: 1px solid grey

.my-card
  width: 100%
  max-width: 350px
</style>
