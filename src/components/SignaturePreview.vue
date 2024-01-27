<template>
  <div class="preview">
    <!--
    <table cellspacing="0" cellpadding="0" border="0">
      <tr>
        <td :width="logoWidth" :style="{'vertical-align': 'middle'}">
          <img :src="logoUrl" :width="logoWidth" :height="logoHeight" :style="{'display': 'block', 'image-rendering': '-webkit-optimize-contrast'}" />
        </td>
        <td width="49">
          <table cellspacing="0" cellpadding="0" border="0" :style="{'margin':'1.5px 0px'}">
            <tr>
              <td width="24" :height="separatorHeight" :style="{'width': '24px'}">&nbsp;</td>
              <td width="1" :height="separatorHeight" :style="{'border-left': '1px solid #d1dbe5'}"></td>
              <td width="24" :height="separatorHeight" :style="{'width': '24px'}">&nbsp;</td>
            </tr>
          </table>
        </td>
        <td>
          <table cellspacing="0" cellpadding="0" border="0">
            <tr>
              <td :style="nameStyle">{{ name }}</td>
            </tr>
            <tr v-if="jobTitle">
              <td :style="jobTitleStyle">{{ jobTitle }}</td>
            </tr>
            <tr>
              <td :style="{'padding': '0px 0px 4px 0px', 'font-size': fontSizeSmall, 'line-height': lineHeightSmall}">
                <table cellspacing="0" cellpadding="0" border="0">
                  <tr>
                    <td v-if="mobile" :style="{'padding': '0px', 'font-family' : fontFamily, 'font-weight': 500, 'font-size': fontSizeSmall, 'line-height': lineHeightSmall, 'color': colorPrimary, 'whitespace': 'nowrap'}">
                      <strong>TEL:</strong> {{ mobile }}
                    </td>
                  </tr>
                </table>
              </td>
            </tr>
          </table>
        </td>
      </tr>
    </table>
    -->
    <table style="color:#202124; width:750px">
      <tbody>
      <tr>
        <td style="width:750px">
          <table>
            <tbody>
            <tr>
              <td><img src="https://drive.google.com/uc?id=1QHBw5kOQQSRcZLo_X6f9IATt45EANQZ0" style="height:130px; margin-right:15px; width:130px" /></td>
              <td>
                <p><strong>{{ name }}</strong></p>

                <p>{{ jobTitle }}<br />
                  WeMatch Consulting GmbH</p>
              </td>
              <td style="width:30px">&nbsp;</td>
              <td style="border-bottom:none; border-left:1px solid #021e26; width:1px">&nbsp;</td>
              <td style="width:15px">&nbsp;</td>
              <td>
                <table>
                  <tbody>
                  <tr>
                    <td>
                      <table>
                        <tbody>
                        <tr>
                          <td><img src="https://i.ibb.co/72d2DPg/phone-icon.png" /></td>
                        </tr>
                        </tbody>
                      </table>
                    </td>
                    <td><a href="'tel:' + mobile" style="color:#021e26;font-size:12px">{{ mobile }}</a></td>
                  </tr>
                  <tr>
                    <td>
                      <table>
                        <tbody>
                        <tr>
                          <td><img src="https://i.ibb.co/9HVnwx4/mail-icon.png" /></td>
                        </tr>
                        </tbody>
                      </table>
                    </td>
                    <td><a href="mailto:a.zeidler@wematch.de" style="color:#021e26;font-size:12px">a.zeidler@wematch.de</a></td>
                  </tr>
                  <tr>
                    <td>
                      <table>
                        <tbody>
                        <tr>
                          <td><img src="https://i.ibb.co/tzsD9mp/webicon.png" /></td>
                        </tr>
                        </tbody>
                      </table>
                    </td>
                    <td><a href="https://wematch.de/" style="color:#021e26;font-size:12px">wematch.de</a></td>
                  </tr>
                  <tr>
                    <td>
                      <table>
                        <tbody>
                        <tr>
                          <td><img src="https://i.ibb.co/8K8fY36/location-icon.png" /></td>
                        </tr>
                        </tbody>
                      </table>
                    </td>
                    <td><span style="color:#021e26"><span style="font-size:12px">N&uuml;rnberger Str. 8, 10787 Berlin</span></span></td>
                  </tr>
                  </tbody>
                </table>
              </td>
            </tr>
            </tbody>
          </table>
        </td>
      </tr>
      <tr>
        <td style="width:723px">
          <table style="width:734px">
            <tbody>
            <tr>
              <td style="border-bottom:1px solid #021e26; border-left:none; height:1px; width:723px">&nbsp;</td>
            </tr>
            </tbody>
          </table>
        </td>
      </tr>
      <tr>
        <td style="width:723px">
          <table style="width:734px">
            <tbody>
            <tr>
              <td style="vertical-align:top"><a href="https://www.wematch.de/"><img src="https://i.ibb.co/W0KgRCF/wematch-logo-1.png" /></a></td>
              <td>&nbsp;</td>
              <td style="width:205.156px"><a href="https://www.linkedin.com/in/anel-zeidler-488257232/" style="padding:0px; float:right" target="_blank"><img alt="linkedin" src="https://i.ibb.co/SQ560NH/linkedin-icon-1.png" /></a></td>
              <td style="width:1px">&nbsp;</td>
            </tr>
            </tbody>
          </table>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'SignaturePreview',
  props: ['companies', 'form'],
  data() {
    return {
      separatorHeight: 64,
      colorPrimary: '#002848',
      fontFamily: "Roboto, sans-serif",
      fontSizeSmall: '10px',
      lineHeightSmall: '12px',
      logoUrl: '',
      logoWidth: 0,
      logoHeight: 62
    }
  },
  mounted() {
    this.preloadCompanyLogos();
    this.parseLogo(this.companyLogo)
  },
  methods: {
    preloadCompanyLogos() {
      this.companies.forEach((com) => {
        let image = new Image();
        image.src = com.logo;
      });
    },
    parseLogo(url){
      let image = new Image();
      image.src = url;
      image.onload = (e) => {
        this.logoUrl = e.target.src
        if (e.target.height > this.logoHeight) {
          this.logoWidth = Math.round(e.target.width * ( this.logoHeight / e.target.height))
        }

        console.log(this.logoWidth)
      }
    }
  },
  watch : {
    companyLogo(nv) {
      this.parseLogo(nv)
    }
  },
  computed: {
    nameStyle() {
      return {
        'font-family' : this.fontFamily, 
        'font-weight': 700, 
        'font-size': '16px', 
        'line-height': '19px', 
        'color': this.colorPrimary, 
        'whitespace': 'nowrap', 
        'padding': '0px 0px 4px 0px'
      }
    },
    jobTitleStyle() {
      return {
        'font-family' : this.fontFamily, 
        'font-weight': 700, 
        'font-size': this.fontSizeSmall, 
        'line-height': this.lineHeightSmall, 
        'color': '#AEC0D1', 
        'whitespace': 'nowrap', 
        'padding': '0px 0px 4px 0px', 
        'text-transform': 'uppercase'
      }
    },
    company() {
      if (this.form.company) {
        return this.companies.find((c) => c.name === this.form.company)
      }
      return {name: '', url: '', logo: ''};
    },
    companyLogo() {
      return this.company.logo
    },
    companyUrl() {
      return this.company.url;
    },
    companyUrlReadable() {
      return this.companyUrl.replace(/(^\w+:|^)\/\//, '');
    },
    name() {
      if ( ! this.form.name.trim()) {
        return 'First Last';
      }

      return this.form.name.trim();
    },
    jobTitle() {
      if (! this.form.jobTitle) {
        return 'Job Title';
      }

      return this.form.jobTitle.trim();
    },
    office() {
      let office = this.form.office.trim();
      if (office === '+') {
        return '';
      }

      return office
    },
    mobile() {
      let mobile = this.form.mobile.trim();
      if (mobile === '+') {
        return '';
      }

      return mobile
    }
  }
}
</script>

<style>
.preview,
.preview.box{
    padding: 20px;
}
.preview-buttons{
    margin-top: 15px;
    margin-left: 20px;
}
.preview-buttons button + button {
    margin-left: 10px;
}
@media (max-width: 919px) {
    .preview{
        display: inline-block;
    }
}
</style>