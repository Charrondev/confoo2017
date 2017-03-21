## New HTML5 Elements

#### The web is changing rapidly
* Ajax
* Web platform maturing
* Screens getting smaller and larger, rounder, wider, taller and wearable
* Pointing devices becoming larger (fingers)
* Access to more hardware features
* People using web browsers on the go.
* Power consumption becoming an important concern.

#### Things we can do
* Access device sensors like gyroscope, compass, light meter, GPS, camera, microphone
* Control device outputs like the speaker, vibration motor and screen.
* Establish more control of what enviroment the program is running in

### Page Visibility
Enables us to programatticlly dtermine fi a page is currently visible.

A page might be hidden if the window is minimised, if the page is in a background tab etc

```
const visible = !document.hidden

// listen for changes
document.addEventListener(visibilitychange, () => {
    console.log("Something")
})
```

#### When is it useful
* Stopping 'expensive' operations like animation
* Ensuring the user sees important information liek flash notifications or alerts
* Pausing media, where appropriate

### Device Orientation
DOM events that provide information about the physical *orientation* and *motion* of a device.

Mostly usable in phones and tablets.

Allows us to detect physical movemens like roation around a point and rate of rotation, not to be confused with the physical orientation of the device.

#### When is it useful
* Good for creating  'physical world' interactions
* It's the same sensors facebook ses for displaying panoramas on mobile
* Could be used for game control
* Makes physical gestures possible (e.g. shake for undo)
* Align a map to match reality

### Battery Status
Enables to programmaticly monitor battery events in a promise based API

```
navigator.getBattery()
    .then((battery) => {
        battery.addEventListener('levelchange', (event) => {
            // Do something here
        })

        if (battery.charging) {}

        battery.chargingTime
        battery.dischargingTime
    })
```

* Scale back on battery intensive actions
* You might chose to save users progress to a server or local storage if the battery is critically low.
* Network polls less frequently on low battery

### Vibration
Gives access to the vibration motor of device. Usually in phones or tablets. Designed for simple tactile feedback only.

### Notifications
Send push notification. Users can easily block this permissions

### WebMidi
[Spec](https://webaudio.github.io/web-midi-api/)

#### WebAudio

#### WebPayment

#### Clipboard