<script setup>
  import {ref, onMounted} from 'vue'
  import InputCard from './components/InputCard.vue'


  const page = ref(0)

  const msg = ref("")

  const pages = ['start', 'risk', 'history','strepa','major','minor','summary']

  const start = ref(
    {
      title: "Acute Rheumatic Fever Calculator",
      subtitle: "Based on Modified Jones Criteria adapted in Australia Guidelines",
      leadout: [],
      disclaimer: ["WARNING:", "This experimental software is NOT approved for diagnostic purposes."],
      next: "Start",
      prev: "",
      items: [],
      selected: [],
    }
  )

  const risk = ref(
    {
      title: "Environmental Risk Profile",
      subtitle: "Select any environmental risk criteria:",
      leadout: ["Aboriginal and Torres Strait Islander peoples living in urban settings, Māori and Pacific Islanders, and potentially immigrants from developing countries, may also be at high risk."],
      disclaimer: [],
      next: "Next",
      prev: "Prev",
      items: [
        {
          label: "In a community with high rates of ARF ( > 30/100,000 per year in 5-14-year-olds)" , 
          value: "arf-risk",
          show: true
        },
        {
          label: "In a community with high rates of RHD ( > 2/1000 all-age prevalence )" , 
          value: "rhd-risk",
          show: true
        },
        {
          label: "An Aboriginal or Torres Strait Islander person in a rural or remote setting", 
          value: "indigenous-remote",
          show: true
        },
        {
          label: "In another potential high risk setting for ARF/RHD (see guidance below)", 
          value: "general-risk",
          show: true
        }
      ],
      selected: [],
    }
  )

const history = ref(
  {
    title: "History of ARF or RHD",
      subtitle: "Select where documented history of ARF or RHD:",
      leadout: ["Only select where a documented history of ARF or RHD exists"],
      disclaimer: [],
      next: "Next",
      prev: "Prev",
      items: [
        {
          label: "Patient has history of ARF or RHD" , 
          value: "priorhistory",
          show: true
        }
      ],
      selected: [],
    }
  )
  



const strepa = ref(
    {
      title: "Strep A Infection",
      subtitle: "Select where evidence of prior infection:",
      leadout: ["Elevated or rising antistreptolysin O or other streptococcal antibody, or a positive throat culture or rapid antigen or nucleic acid test for Strep A infection"],
      disclaimer: [],
      next: "Next",
      prev: "Prev",
      items: [
        {
          label: "Evidence of preceding Strep A infection" , 
          value: "strepa",
          show: true
        }
      ],
      selected: [],
    }
  )
  const major = ref(
    {
      title: "Major Manifestations",
      subtitle: "Select where relevant:",
      leadout: [
        "A definite history of arthritis is sufficient to satisfy Polyarthritis manifestation.",
        "Chorea does not require other manifestations or evidence of preceding Strep A infection, provided other causes of chorea are excluded",
        "Care should be taken not to label other rashes, particularly non-specific viral exanthems, as erythema marginatum."
      ],
      disclaimer: [],
      next: "Next",
      prev: "Prev",
      selected: [],
      items: [
        {label: "Carditis (including subclinical evidence of rheumatic valvulitis on echocardiogram)" , value: "carditis",  show: true},
        {label: "Polyarthritis OR aseptic monoarthritis OR polyarthralgia" , value: "polyarth-hi",  show: true},
        {label: "Polyarthritis" , value: "polyarth-lo",  show: true},
        {label: "Sydenham chorea" , value: "chorea",  show: true},
        {label: "Erythema marginatum" , value: "erythema",  show: true},
        {label: "Subcutaneous nodules" , value: "nodules",  show: true},
     ]
    }
  )
  const minor = ref(
    {
      title: "Minor Manifestations",
      subtitle: "Select where relevant:",
      leadout: [
        "In high-risk groups, fever can be considered a minor manifestation based on a reliable history (in the absence of documented temperature) if anti-inflammatory medication has already been administered."
      ],
      disclaimer: [],
      next: "Next",
      prev: "Prev",
      selected: [],
      items: [  
        {label: "Fever &ge; 38&deg; C" , value: "fever-hi",  show: true},
        {label: "Fever &ge; 38.5&deg; C" , value: "fever-lo",  show: true},
        {label: "Monoarthralgia" , value: "arth-hi",  show: true},
        {label: "Polyarthralgia or aseptic monoarthritis" , value: "arth-lo",  show: true},
        {label: "ESR &ge;30 mm/h OR CRP &ge;30 mg/L" , value: "esr-hi",  show: true},
        {label: "ESR &ge;60 mm/h OR CRP &ge;30 mg/L" , value: "esr-lo",  show: true},
        {label: "Prolonged P-R interval on ECG" , value: "prolonged-pr",  show: true},
      ]
    }
  )

  const summary = ref(
    {
      title: "Calculated Outcome",
      subtitle: "Calculated based on prior selections using 2020 Australian Criteria for ARF Diagnosis",
      statement: "",
      leadout: [],
      disclaimer: ["WARNING:", "This experimental software is NOT approved for diagnostic purposes."],
      next: "Close",
      prev: "Prev",
      selected: [],
      items: []
    }
  )



function changePage( dir ) {
  const ishighrisk = (risk.value.selected.length > 0) ? true : false;
  const hascarditis = major.value.selected.includes('carditis')
  const hasarthritis = major.value.selected.includes('polyarth-hi') || major.value.selected.includes('polyarth-lo')
  for (let item of major.value.items) {
    if (item.value == "polyarth-hi") {
      item.show = ishighrisk;
    }
    if (item.value == "polyarth-lo") {
      item.show = !ishighrisk;
    }
  }
  for (let item of minor.value.items) {
    if ((item.value == "fever-hi") || (item.value == "esr-hi") || (item.value == "arth-hi")) {
      item.show = ishighrisk
    }
    if ((item.value == "fever-lo") || (item.value == "esr-lo") || (item.value == "arth-lo")) {
      item.show = !ishighrisk
    }
    if (item.value == "prolonged-pr") {
      item.show = !hascarditis
    }
    if (item.value == "arth-hi") {
      item.show = ishighrisk && !hasarthritis
    }
    if (item.value == "arth-lo") {
      item.show = !ishighrisk && !hasarthritis
    }
  }
  let nextPage = page.value + dir;
  if ((nextPage >= pages.length) || (nextPage < 0)) {
    nextPage = 0;
  }
  switch (pages[nextPage]) {
    case 'start':
      risk.value.selected = [];
      history.value.selected = [];
      strepa.value.selected = [];
      major.value.selected = [];
      minor.value.selected = [];
      summary.value.leadout = [];
      break;
    case 'summary':
      let risklevel = (risk.value.selected.length > 0) ? "High" : "Low";
      let hadstrep = strepa.value.selected.length > 0;
      let priorARF = history.value.selected.length > 0;
      let nmajor = major.value.selected.length;
      let nminor = minor.value.selected.length;
      let episode = (history.value.selected.length > 0) ? "Recurrent Episode" : "Initial Episode";
      let lines = [];
      lines.push(risklevel + ' risk environment for ARF');
      if (priorARF) {
        lines.push('Documented history of ARF or RHD')
      }
      if (hadstrep) {
        lines.push('Evidence of previous Strep A infection');
      }
      lines.push(nmajor.toString() + ' major manifestations');
      lines.push(nminor.toString() + ' minor manifestations');
      lines.push(' ');
      if ( (hadstrep && (nmajor >= 2)) || (hadstrep && (nmajor ==1) && (nminor >= 2)) || (priorARF && (nminor >= 3)) ) {
        summary.value.statement = 'Indicates a Definite ' + episode + ' of ARF';
      } else if ( (hadstrep && (nmajor == 1)) || (hadstrep && (nmajor ==1) && (nminor == 1)) || (nmajor >= 2) || ((nmajor ==1) && (nminor >= 2))) {
        summary.value.statement = 'Indicates a Probable or Possible ' + episode + ' of ARF';
      } else {
        summary.value.statement = 'Insufficient evidence for ' + episode + ' of ARF';
      }
      lines.push(' ');
      lines.push(' ');
      summary.value.leadout = lines;
      break;
  }
  page.value = nextPage;
}

</script>

<template>
  <v-app>
    <v-app-bar height="50" flat></v-app-bar>
    <v-main class="align-center justify-center" style="min-height: 300px;">
 
    <InputCard 
      v-if="pages[page] === 'start'" 
      v-model="start.selected"
      :cinfo="start" 
      @to-page="changePage"
    />

    <InputCard 
      v-if="pages[page] === 'risk'" 
      v-model="risk.selected" 
      :cinfo="risk" 
      @to-page="changePage"
    />

    
    <InputCard 
      v-else-if="pages[page] === 'history'" 
      v-model="history.selected" 
      :cinfo="history" 
      @to-page="changePage"
    />

    <InputCard 
      v-else-if="pages[page] === 'strepa'" 
      v-model="strepa.selected" 
      :cinfo="strepa" 
      @to-page="changePage"
    />

    <InputCard 
      v-else-if="pages[page] === 'major'" 
      v-model="major.selected" 
      :cinfo="major" 
      @to-page="changePage"
    />
    
    <InputCard 
      v-else-if="pages[page] === 'minor'" 
      v-model="minor.selected" 
      :cinfo="minor" 
      @to-page="changePage"
    />

    <InputCard 
      v-else-if="pages[page] === 'summary'" 
      v-model="summary.selected" 
      :cinfo="summary" 
      @to-page="changePage"
    />

  </v-main>

    <AppFooter />
  </v-app>
</template>

