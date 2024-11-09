<script setup>
  import DetectionEvent from './components/DetectionEvent.vue';
  import SettingsTab from './components/SettingsTab.vue';
  import OctoDevice from './components/OctoDevice.vue';
  import SettingDropdown from './components/SettingDropdown.vue';
  import WebHeader from './components/WebHeader.vue';
  import TabMenu from './components/TabMenu.vue';
  import TabDisplay from './components/TabDisplay.vue';
  import TabUnit from './components/TabUnit.vue';
  import OptionDrop from './components/OptionDrop.vue';
  import OptionSection from './components/OptionSection.vue';
  import SettingsDisplay from './components/SettingsDisplay.vue';

  let eventCount = 0;
</script>

<script>
  let curId = "OCTOviewCamera";
  let curDevice = "OCTOview";

  function showStuff(id) {
    console.log(curId,id);
    document.getElementById(curId.concat('Pane')).style.display = 'none';
    document.getElementById(curId).style.backgroundColor = 'rgb(24, 24, 27)';
    document.getElementById(curId).style.backgroundColor = '';
    document.getElementById(id.concat('Pane')).style.display = 'block';
    document.getElementById(id).style.backgroundColor =  'rgb(39, 39, 42)';
    curId = id;
  }

  function filterEvents(device) {
    console.log(curDevice,device);
    showStuff(device+"Camera");
    document.getElementById("Device"+curDevice).style.backgroundColor = 'rgb(24, 24, 27)';
    document.getElementById("Device"+device).style.backgroundColor =  'rgb(39, 39, 42)';

    document.getElementById(curDevice+"SettingsPanes").style.display = "none";
    document.getElementById(device+"SettingsPanes").style.display = "flex";

    document.getElementById(curDevice+"Disp").style.display = "none";
    document.getElementById(device+"Disp").style.display = "block";

    curDevice = device;
    curId = device+"Camera";

    if (device == "OCTOview") {
      for (let i = 0, len = document.querySelectorAll('[id*="Event"]').length; i < len; i++) {
        document.querySelectorAll('[id*="Event"]')[i].style.display = 'block';
      }
    }
    else {
      for (let i = 0, len = document.querySelectorAll('[id*="Event"]').length; i < len; i++) {
        document.querySelectorAll('[id*="Event"]')[i].style.display = 'none';
      }
      for (let i = 0, len = document.querySelectorAll('[id*="Event'.concat(device) + '"]').length; i < len; i++) {
        document.querySelectorAll('[id*="Event'.concat(device) + '"]')[i].style.display = 'block';
      }
    }
  }
</script>

<template>    
  <WebHeader alert="Live Event" />

  <div class="flex flex-col shrink h-screen m-2 lg:mx-56">
    <div class="mt-2 bg-zinc-900 rounded-t-xl">

      <ol class="text-white font-sans font-semi select-none flex flex-wrap justify-between">
        <div class="flex flex-wrap w-fit">
          <OctoDevice class="rounded-t-2xl" style="background-color: rgb(39, 39, 42);" id="DeviceOCTOview" name="OCTOview" @click="filterEvents('OCTOview')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceOCTO" name="OCTO" @click="filterEvents('OCTO')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 1" name="Quad 1" @click="filterEvents('Quad 1')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 2" name="Quad 2" @click="filterEvents('Quad 2')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 3" name="Quad 3" @click="filterEvents('Quad 3')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 4" name="Quad 4" @click="filterEvents('Quad 4')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 5" name="Quad 5" @click="filterEvents('Quad 5')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 6" name="Quad 6" @click="filterEvents('Quad 6')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 7" name="Quad 7" @click="filterEvents('Quad 7')" />
          <OctoDevice class="rounded-t-2xl" id="DeviceQuad 8" name="Quad 8" @click="filterEvents('Quad 8')" />
        </div>
        <a class="align-middle float-right px-2 pt-1 text-xs rounded-xl hover:bg-zinc-700" href="#"><img class="h-4 inline mt-1 mr-1 pb-1 mb-1" src="./assets/img/mag.webp" alt="search button">Filter</a>
      </ol>
    </div>

    <div class="flex flex-row justify-center text-center text-white font-mono text-lg">
      <div class="w-full bg-zinc-800 mb-1">

        <h1 class="font-sans font-semibold text-sm py-0.5 border-b border-zinc-900">Events</h1>

        <div class="flex flex-row overflow-x-auto min-h-36">
          <DetectionEvent id="EventOCTO 1" date="10/55/24" time="11:34am" unit="OCTO" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 1 2" date="10/11/24" time="11:34am" unit="Quad 1" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 1 3" date="10/11/24" time="11:34am" unit="Quad 1" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 1 4" date="10/11/24" time="11:34am" unit="Quad 1" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 2 5" date="10/11/24" time="11:34am" unit="Quad 2" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 2 6" date="10/11/24" time="11:34am" unit="Quad 2" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 2 7" date="10/11/24" time="11:34am" unit="Quad 2" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 3 8" date="10/11/24" time="11:34am" unit="Quad 3" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 4 9" date="10/11/24" time="11:34am" unit="Quad 4" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 5 0" date="10/11/24" time="11:34am" unit="Quad 5" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 6 1" date="10/11/24" time="11:34am" unit="Quad 6" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
          <DetectionEvent id="EventQuad 7 2" date="10/11/24" time="11:34am" unit="Quad 7" device="PTZ 5" eventType="Person Detected"><img class="h-20 w-auto m-auto rounded hover:blur-sm" src="./assets/img/parking_cam.jpg" alt="Detection Event"></DetectionEvent>
        </div>
      </div>
    </div>

    <div class="h-2/5 flex justify-center align-middle bg-zinc-800 rounded-b my-1 -mt-1 border-t-2 border-zinc-900 ">
      <img id="OCTOviewDisp" class="p-6" src="./assets/img/parking_cam.jpg" alt="a low poly horse">
      <img id="OCTODisp" class="p-6 hidden" src="./assets/img/lot1.jpg" alt="a low poly horse">
      <img id="Quad 1Disp" class="p-6 hidden" src="./assets/img/lot2.jpg" alt="a low poly horse">
      <img id="Quad 2Disp" class="p-6 hidden" src="./assets/img/lot3.png" alt="a low poly horse">
      <img id="Quad 3Disp" class="p-6 hidden" src="./assets/img/lot4.png" alt="a low poly horse">
      <img id="Quad 4Disp" class="p-6 hidden" src="./assets/img/lot5.jpg" alt="a low poly horse">
      <img id="Quad 5Disp" class="p-6 hidden" src="./assets/img/lot6.jpg" alt="a low poly horse">
      <img id="Quad 6Disp" class="p-6 hidden" src="./assets/img/lot7.jpg" alt="a low poly horse">
      <img id="Quad 7Disp" class="p-6 hidden" src="./assets/img/lot8.png" alt="a low poly horse">
      <img id="Quad 8Disp" class="p-6 hidden" src="./assets/img/lot9.jpg" alt="a low poly horse">
    </div>

    <div class=" h-1/4 text-white bg-zinc-900 rounded my-1 mt-1">
      <div class="flex flex-col h-full" id="OCTOviewSettingsPanes">

        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="OCTOviewCamera" @click="showStuff('OCTOviewCamera')" />
          <SettingsTab name="Audio" id="OCTOviewAudio" @click="showStuff('OCTOviewAudio')" />
          <SettingsTab name="Device" id="OCTOviewDevice" @click="showStuff('OCTOviewDevice')" />
          <SettingsTab name="Advanced" id="OCTOviewAdvanced" @click="showStuff('OCTOviewAdvanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="OCTOviewCameraPane">
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="Hamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTOviewAudioPane">
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="bHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTOviewDevicePane">
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="cHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTOviewAdvancedPane">
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="dHamburger" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="OCTOSettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="OCTOCamera" @click="showStuff('OCTOCamera')" />
          <SettingsTab name="Audio" id="OCTOAudio" @click="showStuff('OCTOAudio')" />
          <SettingsTab name="Device" id="OCTODevice" @click="showStuff('OCTODevice')" />
          <SettingsTab name="Advanced" id="OCTOAdvanced" @click="showStuff('OCTOAdvanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="OCTOCameraPane">
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOA" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTOAudioPane">
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOB" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTODevicePane">
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOC" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="OCTOAdvancedPane">
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="OCTOD" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 1SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 1Camera" @click="showStuff('Quad 1Camera')" />
          <SettingsTab name="Audio" id="Quad 1Audio" @click="showStuff('Quad 1Audio')" />
          <SettingsTab name="Device" id="Quad 1Device" @click="showStuff('Quad 1Device')" />
          <SettingsTab name="Advanced" id="Quad 1Advanced" @click="showStuff('Quad 1Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 1CameraPane">
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 1AudioPane">
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 1DevicePane">
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 1AdvancedPane">
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad1D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 2SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 2Camera" @click="showStuff('Quad 2Camera')" />
          <SettingsTab name="Audio" id="Quad 2Audio" @click="showStuff('Quad 2Audio')" />
          <SettingsTab name="Device" id="Quad 2Device" @click="showStuff('Quad 2Device')" />
          <SettingsTab name="Advanced" id="Quad 2Advanced" @click="showStuff('Quad 2Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 2CameraPane">
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 2AudioPane">
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 2DevicePane">
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 2AdvancedPane">
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 3SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 3Camera" @click="showStuff('Quad 3Camera')" />
          <SettingsTab name="Audio" id="Quad 3Audio" @click="showStuff('Quad 3Audio')" />
          <SettingsTab name="Device" id="Quad 3Device" @click="showStuff('Quad 3Device')" />
          <SettingsTab name="Advanced" id="Quad 3Advanced" @click="showStuff('Quad 3Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 3CameraPane">
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 3AudioPane">
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 3DevicePane">
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad2C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 3AdvancedPane">
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad3D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 4SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 4Camera" @click="showStuff('Quad 4Camera')" />
          <SettingsTab name="Audio" id="Quad 4Audio" @click="showStuff('Quad 4Audio')" />
          <SettingsTab name="Device" id="Quad 4Device" @click="showStuff('Quad 4Device')" />
          <SettingsTab name="Advanced" id="Quad 4Advanced" @click="showStuff('Quad 4Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 4CameraPane">
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 4AudioPane">
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 4DevicePane">
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 4AdvancedPane">
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad4D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 5SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 5Camera" @click="showStuff('Quad 5Camera')" />
          <SettingsTab name="Audio" id="Quad 5Audio" @click="showStuff('Quad 5Audio')" />
          <SettingsTab name="Device" id="Quad 5Device" @click="showStuff('Quad 5Device')" />
          <SettingsTab name="Advanced" id="Quad 5Advanced" @click="showStuff('Quad 5Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 5CameraPane">
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 5AudioPane">
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 5DevicePane">
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 5AdvancedPane">
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad5D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 6SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 6Camera" @click="showStuff('Quad 6Camera')" />
          <SettingsTab name="Audio" id="Quad 6Audio" @click="showStuff('Quad 6Audio')" />
          <SettingsTab name="Device" id="Quad 6Device" @click="showStuff('Quad 6Device')" />
          <SettingsTab name="Advanced" id="Quad 6Advanced" @click="showStuff('Quad 6Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 6CameraPane">
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 6AudioPane">
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 6DevicePane">
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 6AdvancedPane">
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad6D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 7SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 7Camera" @click="showStuff('Quad 7Camera')" />
          <SettingsTab name="Audio" id="Quad 7Audio" @click="showStuff('Quad 7Audio')" />
          <SettingsTab name="Device" id="Quad 7Device" @click="showStuff('Quad 7Device')" />
          <SettingsTab name="Advanced" id="Quad 7Advanced" @click="showStuff('Quad 7Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 7CameraPane">
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 7AudioPane">
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 7DevicePane">
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 7AdvancedPane">
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad7D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>

      <div class="flex-col h-full hidden" id="Quad 8SettingsPanes">
        <TabMenu>
          <SettingsTab style="background-color: rgb(39, 39, 42);" name="Camera" id="Quad 8Camera" @click="showStuff('Quad 8Camera')" />
          <SettingsTab name="Audio" id="Quad 8Audio" @click="showStuff('Quad 8Audio')" />
          <SettingsTab name="Device" id="Quad 8Device" @click="showStuff('Quad 8Device')" />
          <SettingsTab name="Advanced" id="Quad 8Advanced" @click="showStuff('Quad 8Advanced')" />
        </TabMenu>

        <div class="h-full bg-zinc-800">
          <SettingsDisplay id="Quad 8CameraPane">
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8A" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 8AudioPane">
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8B" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 8DevicePane">
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8C" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>

          <SettingsDisplay class="hidden" id="Quad 8AdvancedPane">
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
            <SettingDropdown name="quad8D" :selections="['lettuce','tomato','ketchup','mustard']"/>
          </SettingsDisplay>
        </div>
      </div>


    </div>
  </div>
</template>