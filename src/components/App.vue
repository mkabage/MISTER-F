<template>
  <div id="app">
    <img src="../../assets/brand-logo.png" style="margin-left: 43%">
    <div>
      <nav class="container navbar navbar-expand-lg navbar-light bg-light">
        <router-link to="/">
          Boquets
        </router-link>
        <ul
          class="navbar-nav"
          style="width: 100%;"
        >
          <li class="nav-item">
            <router-link
              class="nav-link"
              to="/about"
            >
              About us
            </router-link>
          </li>
          <li
            class="nav-item"
            style="margin-right: 490px"
          >
            <router-link
              class="nav-link"
              to="/contact"
            >
              Contact
            </router-link>
          </li>

          <div class="col-md-4">
            <li class="nav-item right">
              <router-link
                class="nav-link"
                to="/help"
              >
                Help
              </router-link>
            </li>
            <li class="nav-item right">
              <a
                v-if="isLogin()"
                class="nav-link"
                @click="logoutBtn"
              >Logout</a>
              <router-link
                v-else
                class="nav-link"
                to="/login"
              >
                Login
              </router-link>
            </li>

            <li class="nav-item right">
              <router-link
                class="nav-link"
                to="/dashboard"
              >
                Cart
              </router-link>
            </li>
          </div>
        </ul>
      </nav>
    </div>

    <hr>
    <router-view />

    <hr>

    <div style="margin-left: 80px">
      <div class="row footer">
        <div
          class="col-md-2"
          style="text-align: left;"
        >
          <b>Mister Fluers</b>
          <div>
            <router-link to="/">
              Home
            </router-link>
          </div>
          <div>
            <router-link to="/about">
              About us
            </router-link>
          </div>
          <div>
            Concept
          </div>
          <div>
            <router-link to="/contact">
              Contact us
            </router-link>
          </div>
        </div>

        <div
          class="col-md-8 social-plugins"
          style="padding: 77px; text-align: center;"
        >
          <div>
            <font-awesome-icon :icon="['fab', 'twitter']" />
            <font-awesome-icon :icon="['fab', 'facebook']" />
            <font-awesome-icon :icon="['fab', 'pinterest']" />
            <font-awesome-icon :icon="['fab', 'instagram']" />
          </div>

          <div>
            COPYRIGHT 2018 MISTER FLUERS
          </div>
        </div>

        <div
          class="col-md-2"
          style="text-align: left;"
        >
          <b>Services</b>
          <div>
            <router-link to="/">
              Bouquets
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  methods: {
    logoutBtn (e) {
      this.logout()
      this.$router.push('/')
    }
  }
}
</script>

<style lang="scss">
  hr{
      font-weight: bold;
      border: 1px solid black !important;
      margin-bottom: 60px !important;
  }

  .nav-link{
      cursor: pointer;
  }

  @media(max-width: 960px){
      .nav-link{
          float: left;
      }
  }

  .brand-text{
      line-height: 3em;
      font-weight: bold;
      padding-top: 90px;
      padding-left: 80px;
      font-size: 25px;
      text-align: left;
  }

  #app .bg-light{
      background-color: white !important;
  }

  #app nav .nav-item{
      font-weight: bold;
      padding: 0 5px;
  }

  #app{
      .router-link-active{
          font-weight: bold;
          color: blue($color: #000000)
          // padding: 0 20px;
      }

      .right{
          float: right;
      }
  }

  #app #faq{
      // FAQ
      .faq-nav {
          flex-direction: column;
          margin: 0 0 32px;
          border-radius: 2px;
          border: 1px solid #ddd;
          box-shadow: 0 1px 5px rgba(85, 85, 85, 0.15);

          .nav-link {
              position: relative;
              display: block;
              margin: 0;
              padding: 13px 16px;
              background-color: #fff;
              border: 0;
              border-bottom: 1px solid #ddd;
              border-radius: 0;
              color: #616161;
              transition: background-color .2s ease;

              &:hover {
                  background-color: #f6f6f6;
              }

              &.active {
                  background-color: #f6f6f6;
                  font-weight: 700;
                  color: rgba(0,0,0,.87);
              }

              &:last-of-type {
                  border-bottom-left-radius: 2px;
                  border-bottom-right-radius: 2px;
                  border-bottom: 0;
              }

              i.mdi {
                  margin-right: 5px;
                  font-size: 18px;
                  position: relative;
              }
          }
      }

      // TAB CONTENT
      .tab-content {
          box-shadow: 0 1px 5px rgba(85, 85, 85, 0.15);

          .card {
              border-radius: 0;
          }

          .card-header {
              padding: 15px 16px;
              border-radius: 0;
              background-color: #f6f6f6;

              h5 {
                  margin: 0;

                  button {
                      display: block;
                      width: 100%;
                      padding: 0;
                      border: 0;
                      font-weight: 700;
                      color: rgba(0,0,0,.87);
                      text-align: left;
                      white-space: normal;

                      &:hover,
                      &:focus,
                      &:active,
                      &:hover:active {
                          text-decoration: none;
                      }
                  }
              }
          }

          .card-body {
              p {
                  color: #616161;

                  &:last-of-type {
                      margin: 0;
                  }
              }
          }
      }

      // BORDER FIX
      .accordion {
          > .card {
              &:not(:first-child) {
                  border-top: 0;
              }
          }
      }

      .collapse.show {
          .card-body {
              border-bottom: 1px solid rgba(0,0,0,.125);
          }
      }

      .collapse:not(.show){
          display: block;
      }
  }

  #login-form{
      text-align: left;
  }

  #app .footer{
      a {
          color: black;
          font-weight: normal;
      }

      svg{
          font-size: 26px;
          margin-left: 20px;
      }
  }

  #app .contact-us{
    text-align: center;
      form{
          label{
              text-align: left !important;
          }
      }
  }

  .pointer{
      cursor: pointer;
  }
</style>
