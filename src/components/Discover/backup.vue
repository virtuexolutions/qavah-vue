<template>
  <div class="discover-page">
    <b-overlay :show="ready">
      <Tinder
        ref="tinder"
        key-name="id"
        :queue.sync="queue"
        :offset-y="10"
        @submit="onSubmit"
      >
        <template slot-scope="scope">
          <div class="swiping-card-row-web">
            <div class="main">
              {{ scope.data }}
              <!-- Right -->
              <div class="right">
                <vue-perfect-scrollbar
                  class=""
                  :settings="{
                    suppressScrollX: true,
                    wheelPropagation: false,
                  }"
                  ref="webLeftScroll1"
                >
                  <div class="mb-4">
                    <h4>Beliefs</h4>

                    <div class="beliefs-tags-container">
                      <b-badge
                        class="belief-tag"
                        variant="empty"
                        pill
                        v-for="(tag, index) in scope.data.beliefs"
                        :key="index"
                      >
                        {{ tag }}
                      </b-badge>
                    </div>
                  </div>

                  <div class="mb-4">
                    <h4>Values</h4>

                    <div class="values-tags-container">
                      <b-badge
                        class="value-tag"
                        variant="empty"
                        pill
                        v-for="(tag, index) in scope.data.values"
                        :key="index"
                      >
                        {{ tag }}
                      </b-badge>
                    </div>
                  </div>

                  <div class="mb-4">
                    <h4>Passions</h4>
                    <div class="passions-tags-container">
                      <b-badge
                        class="passion-tag"
                        variant="empty"
                        pill
                        v-for="(tag, index) in scope.data.passions"
                        :key="index"
                      >
                        {{ tag }}
                      </b-badge>
                    </div>
                  </div>
                </vue-perfect-scrollbar>
              </div>

              <!-- Middle -->
              <div class="middle">
                <div
                  class="image"
                  v-bind:style="{ backgroundImage: scope.data.thumbnail }"
                ></div>

                <div class="info">
                  <p class="title p-0 m-0">{{ scope.data.name }}</p>
                  <p class="subtitle p-0 m-0">
                    {{ scope.data.age }} - {{ scope.data.location }}
                  </p>
                  <p class="subtitle p-0 m-0">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      height="20"
                      viewBox="0 0 20 20"
                      fill="currentColor"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z"
                        clip-rule="evenodd"
                      />
                    </svg>
                    {{ scope.data.geolocation }}
                  </p>
                </div>
              </div>

              <!-- Left -->
              <div class="left">
                <vue-perfect-scrollbar
                  class=""
                  :settings="{
                    suppressScrollX: true,
                    wheelPropagation: false,
                  }"
                  ref="webRightScroll1"
                >
                  <div class="">
                    <!-- Basic Info -->
                    <div class="mb-4">
                      <span class="top-picks-btn">
                        <svg
                          xmlns="http://www.w3.org/2000/svg"
                          xmlns:xlink="http://www.w3.org/1999/xlink"
                          enable-background="new 0 0 91 91"
                          height="25"
                          class="mr-2"
                          id="Layer_1"
                          version="1.1"
                          viewBox="0 0 91 91"
                          xml:space="preserve"
                        >
                          <g>
                            <path
                              d="M88.371,27.674l-8.9,37.584c0,4.646-3.768,8.41-8.411,8.41H30.508c-4.643,0-8.412-3.765-8.412-8.41   l-8.903-37.584L35.947,45.48L50.78,27.674L65.621,45.48L88.371,27.674z"
                              fill="#FDE497"
                            />
                            <path
                              d="M68.693,76.191H22.601c-6.559,0-11.914-5.252-12.08-11.771L0.465,21.969   c-0.248-1.042,0.191-2.127,1.093-2.704c0.902-0.578,2.071-0.522,2.915,0.137L28.41,38.134l15.297-18.361   c0.957-1.147,2.916-1.151,3.875,0l15.302,18.361l23.935-18.732c0.843-0.66,2.011-0.714,2.913-0.138   c0.902,0.578,1.34,1.662,1.094,2.705L80.772,64.42C80.605,70.939,75.252,76.191,68.693,76.191z M7.031,27.808l8.461,35.719   c0.045,0.191,0.067,0.386,0.067,0.582c0,3.881,3.158,7.039,7.041,7.039h46.093c3.881,0,7.04-3.158,7.04-7.039   c0-0.196,0.023-0.391,0.067-0.582l8.459-35.718L64.065,43.613c-1.072,0.841-2.618,0.678-3.491-0.371L45.645,25.327L30.72,43.242   c-0.871,1.047-2.417,1.212-3.491,0.371L7.031,27.808z"
                              fill="#454B53"
                            />
                            <path
                              d="M46.22,51.608c-2.001,0-3.629-1.627-3.629-3.629c0-2,1.628-3.627,3.629-3.627s3.628,1.627,3.628,3.627   C49.848,49.981,48.221,51.608,46.22,51.608z"
                              fill="#454B53"
                            />
                          </g>
                        </svg>
                        Top Pick
                      </span>
                      <h4>Basic Info</h4>

                      <p class="m-0 mt-2 p-0">
                        Gender:
                        <b-badge variant="empty" pill class="left-bubble">{{
                          scope.data.iAm
                        }}</b-badge>
                      </p>

                      <p>
                        Age:
                        <b-badge variant="empty" pill class="left-bubble">{{
                          scope.data.age
                        }}</b-badge>
                      </p>
                    </div>

                    <b-button
                      v-if="scope.data.subscription_type === 'free'"
                      class="custom-btn-1"
                      @click="$router.push('powerups')"
                      variant="primary"
                      >See More Information
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        height="20"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                        stroke-width="2"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
                        /></svg
                    ></b-button>

                    <b-button
                      v-else
                      v-b-toggle.collapse-1
                      class="custom-btn-1"
                      variant="primary"
                      >See More Information
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        height="20"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                        stroke-width="2"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M12 8v4m0 4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
                        /></svg
                    ></b-button>

                    <b-collapse id="collapse-1" class="mt-2">
                      <div class="for-premium">
                        <div class="">
                          <p class="m-0 mt-2 p-0">
                            Height:
                            <b-badge variant="empty" pill class="left-bubble"
                              >6"</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Email:
                            <b-badge variant="empty" pill class="left-bubble"
                              >email</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            About Me:
                            <b-badge variant="empty" pill class="left-bubble"
                              >about</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Body Type:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Few Extra Pounds</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Marital Belief System :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Monogamy</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Relationship looking for:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Sister wife marriage</b-badge
                            >
                          </p>
                        </div>

                        <div class="mb-4">
                          <h6 class="my-4">More About Me</h6>

                          <p class="m-0 mt-2 p-0">
                            Drink ? :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Don’t Drink</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Smoke ? :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Only cannabis</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Employment Status:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Self employed</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Living situation:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Live with family</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Willing to relocate:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Not willing to relocate</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Have Childrens ?:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Yes- They sometimes live at home</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Want Childrens ? :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Not Sure</b-badge
                            >
                          </p>
                        </div>

                        <div class="mb-4">
                          <h5>Isrealite Filters</h5>

                          <h6 class="my-4">Lifestyle</h6>

                          <p class="m-0 mt-2 p-0">
                            I believe I am:
                            <b-badge variant="empty" pill class="left-bubble"
                              >I am a diaspora Israelite</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Any Affiliations :
                            <b-badge variant="empty" pill class="left-bubble"
                              >I go to an assembly</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Spiritual background :
                            <b-badge variant="empty" pill class="left-bubble"
                              >I came out of the Nation of Islam</b-badge
                            >
                          </p>

                          <h6 class="my-4">Study Habits</h6>

                          <p class="m-0 mt-2 p-0">
                            Study Habits :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Torah & Tanakh</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Study Bible :
                            <b-badge variant="empty" pill class="left-bubble"
                              >1611 King James w/Apocrypha</b-badge
                            >
                          </p>

                          <h6 class="my-4">
                            “I Value” Israelite Practice Keeping
                          </h6>

                          <p class="m-0 mt-2 p-0">
                            Marital Status:
                            <b-badge variant="empty" pill class="left-bubble"
                              >Separated</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Spiritual Values :
                            <b-badge variant="empty" pill class="left-bubble"
                              >Non-Messianic</b-badge
                            >
                          </p>

                          <p class="m-0 mt-2 p-0">
                            Israelites Practice Keeping :
                            <b-badge variant="empty" pill class="left-bubble"
                              >New Moons</b-badge
                            >
                          </p>
                        </div>
                      </div>
                    </b-collapse>
                  </div>
                  <!-- More About Me -->
                </vue-perfect-scrollbar>
              </div>
            </div>
          </div>
        </template>
        <img
          class="like-pointer"
          slot="like"
          src="@/assets/Swipe_Stamps/Ken.png"
        />
        <img
          class="nope-pointer"
          slot="nope"
          src="@/assets/Swipe_Stamps/Lo.png"
        />
        <img
          class="super-pointer"
          slot="super"
          src="@/assets/Swipe_Stamps/Superfancy.png"
        />
        <img
          class="rewind-pointer"
          slot="rewind"
          src="@/assets/Swipe_Stamps/Superfancy.png"
        />
      </Tinder>
      <div class="btns">
        <!-- Rewind -->
        <b-button class="action-btn action-btn-1" @click="decide('rewind')">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"
            />
          </svg>
        </b-button>
        <!-- Lo -->
        <b-button class="action-btn action-btn-2" @click="decide('nope')">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </b-button>
        <!-- Superfancy -->
        <b-button class="action-btn action-btn-3" @click="decide('super')">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M11.049 2.927c.3-.921 1.603-.921 1.902 0l1.519 4.674a1 1 0 00.95.69h4.915c.969 0 1.371 1.24.588 1.81l-3.976 2.888a1 1 0 00-.363 1.118l1.518 4.674c.3.922-.755 1.688-1.538 1.118l-3.976-2.888a1 1 0 00-1.176 0l-3.976 2.888c-.783.57-1.838-.197-1.538-1.118l1.518-4.674a1 1 0 00-.363-1.118l-3.976-2.888c-.784-.57-.38-1.81.588-1.81h4.914a1 1 0 00.951-.69l1.519-4.674z"
            />
          </svg>
        </b-button>
        <!-- Ken -->
        <b-button class="action-btn action-btn-4" @click="decide('like')">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"
            />
          </svg>
        </b-button>
        <!-- Skip -->
        <b-button class="action-btn action-btn-5" @click="decide('help')">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="20"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M11.3 1.046A1 1 0 0112 2v5h4a1 1 0 01.82 1.573l-7 10A1 1 0 018 18v-5H4a1 1 0 01-.82-1.573l7-10a1 1 0 011.12-.38z"
              clip-rule="evenodd"
            />
          </svg>
        </b-button>
      </div>

      <!-- Modals -->
      <b-modal id="getQavahPlusModal" centered hide-header hide-footer>
        <div class="top">
          <h2 class="title">Get Qavah Plus</h2>
          <p class="subtitle">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              height="20"
              class="refresh-icon mr-1"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"
              /></svg
            >Unlimited Rewinds , Go back and try again.
          </p>
        </div>
        <div class="pricing-cards">
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">12</p>
              <p class="p-0 m-0 title">Months</p>
            </div>
            <p class="p-0 py-2 m-0 price">20$/mo</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">6</p>
              <p class="p-0 m-0 title">Months</p>
            </div>
            <p class="p-0 py-2 m-0 price">15$/mo</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">1</p>
              <p class="p-0 m-0 title">Month</p>
            </div>
            <p class="p-0 py-2 m-0 price">10$/mo</p>
          </div>
        </div>
        <div class="btn-container">
          <b-button variant="primary">Continue</b-button>
          <b-button variant="empty" @click="$bvModal.hide('getQavahPlusModal')"
            >Cancel</b-button
          >
        </div>
      </b-modal>

      <b-modal id="superLikesModal" centered hide-header hide-footer>
        <div class="top">
          <h2 class="title">Get Qavah Gold</h2>
          <p class="subtitle">5 Superlikes a week</p>
        </div>
        <div class="pricing-cards">
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">12</p>
              <p class="p-0 m-0 title">Months</p>
            </div>
            <p class="p-0 py-2 m-0 price">20$/mo</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">6</p>
              <p class="p-0 m-0 title">Months</p>
            </div>
            <p class="p-0 py-2 m-0 price">15$/mo</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">1</p>
              <p class="p-0 m-0 title">Month</p>
            </div>
            <p class="p-0 py-2 m-0 price">10$/mo</p>
          </div>
        </div>
        <div class="btn-container">
          <b-button variant="primary">Continue</b-button>
          <b-button variant="empty" @click="$bvModal.hide('superLikesModal')"
            >Cancel</b-button
          >
        </div>
      </b-modal>

      <b-modal id="skipTheQueueModal" centered hide-header hide-footer>
        <div class="top">
          <h2 class="title">Skip The Line</h2>
          <p class="subtitle">
            Be a top profile in your area for 30 minutes to get more matches.
          </p>
        </div>
        <div class="pricing-cards">
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">1</p>
              <p class="p-0 m-0 title">Boost</p>
            </div>
            <p class="p-0 py-2 m-0 price">20$/ea</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">5</p>
              <p class="p-0 m-0 title">Boost</p>
            </div>
            <p class="p-0 py-2 m-0 price">15$/ea</p>
          </div>
          <div class="price-card">
            <div class="top">
              <p class="p-0 m-0 quantity">10</p>
              <p class="p-0 m-0 title">Boost</p>
            </div>
            <p class="p-0 py-2 m-0 price">10$/ea</p>
          </div>
        </div>
        <div class="btn-container">
          <b-button class="boost-btn mb-2">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="mr-1"
              height="25"
              viewBox="0 0 20 20"
              fill="currentColor"
            >
              <path
                fill-rule="evenodd"
                d="M12 7a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0V8.414l-4.293 4.293a1 1 0 01-1.414 0L8 10.414l-4.293 4.293a1 1 0 01-1.414-1.414l5-5a1 1 0 011.414 0L11 10.586 14.586 7H12z"
                clip-rule="evenodd"
              />
            </svg>
            Get More Boosts
          </b-button>
          <b-button class="qavah-gold-btn mb-2" variant="primary"
            >Get Qavah Gold</b-button
          >
          <b-button
            class="no-thanks-btn mb-2"
            variant="empty"
            @click="$bvModal.hide('skipTheQueueModal')"
            >No Thanks</b-button
          >
        </div>
      </b-modal>
    </b-overlay>
  </div>
</template>



<style scoped lang="scss">
.discover-page {
  margin: 0;
  background-color: #20262e;
  overflow: hidden;
  min-height: 100vh;
  position: relative;
}

.action-btn {
  outline: none;
  border: none;
  border-radius: 50%;
  padding: 0.8rem;
  background-color: #f1f5f9;
  transition: all ease 0.5s;
  // box-shadow: 20px 20px 60px #bebebe, -20px -20px 60px #ffffff;
  z-index: 9999;

  &:hover {
    transform: scale(110%);
  }

  svg {
    height: 25px;
  }

  &:active {
    background-color: #635dcb !important;
  }
}

.action-btn-1 {
  border: 1px solid #93652b;
  svg {
    stroke: #93652b;
  }
}

.action-btn-2 {
  border: 1px solid #dc2626;
  svg {
    stroke: #dc2626;
    fill: #dc2626;
  }
}

.action-btn-3 {
  border: 1px solid #3acdf5;
  svg {
    stroke: #3acdf5;
    fill: #3acdf5;
  }
}

.action-btn-4 {
  border: 1px solid #2ae4bd;
  svg {
    fill: #2ae4bd;
    stroke: #2ae4bd;
  }
}

.action-btn-5 {
  border: 1px solid #a31fec;
  svg {
    stroke: #a31fec;
    fill: #a31fec;
  }
}

#app .vue-tinder {
  position: absolute;
  z-index: 1;
  left: 0;
  right: 0;
  top: 23px;
  margin: auto;
  width: calc(100% - 20px);
  height: calc(100% - 23px - 65px - 47px - 16px);
  min-width: 70vw;
  max-width: 355px;
}

.nope-pointer,
.like-pointer {
  position: absolute;
  z-index: 1;
  top: 20px;
  width: 64px;
  height: 64px;
}

.nope-pointer {
  right: 10px;
}

.like-pointer {
  left: 10px;
}

.super-pointer {
  position: absolute;
  z-index: 1;
  bottom: 80px;
  left: 0;
  right: 0;
  margin: auto;
  width: 112px;
  height: 78px;
}

.rewind-pointer {
  position: absolute;
  z-index: 1;
  top: 20px;
  right: 10px;
  width: 112px;
  height: 78px;
}

.pic {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

.btns {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 30px;
  margin: auto;
  height: 65px;
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 300px;
  max-width: 355px;
}

.btns img {
  margin-right: 12px;
  box-shadow: 0 4px 9px rgba(0, 0, 0, 0.15);
  border-radius: 50%;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}

.btns img:nth-child(2n + 1) {
  width: 53px;
}

.btns img:nth-child(2n) {
  width: 65px;
}

.btns img:nth-last-child(1) {
  margin-right: 0;
}
</style>