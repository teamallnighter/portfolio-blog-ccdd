---
template: blog-post
title: "Chris Learns Svelte: Meet Up App"
slug: /svelte/meet-us
date: 2020-11-23 05:49
description: Web Design Edmonton, Web Development Edmonton
featuredImage: /assets/screen-shot-2020-11-23-at-5.51.34-am.png
---
## Contact Card Generator

##### Build: Svelte.js | HTML | CSS |JavaScript

##### Features: Dynamic Content

##### Deployment: Netlify

#### [Check it out](https://meet-us-ccdd.netlify.app/)

- - -

In this project we dive deeper into Svelte.js

We create a meet ups app that shares local meet up groups and events. We build multiple custom components and implement them into the app. 

## App.js

```svelte
<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from './UI/Button.svelte';

  let title = "";
  let subtitle = "";
  let address = "";
  let email = "";
  let description = "";
  let imageUrl = "";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup, we will have some experts that teach you how to code!",
      imageUrl:
        "https://www.avenuecalgary.com/wp-content/uploads/2019/01/CentralLibrary1Web-110c740b.jpg",
      address: "800 3 St SE, Calgary, AB T2G 2E7",
      contactEmail: "code@test.com"
    },
    {
      id: "m2",
      title: "Ableton Bootcamp",
      subtitle: "Hosted by Beatdrop",
      description: "Learn the latest features of Ableton 11 and learn some of the more standard features.",
      imageUrl:
        "https://images.squarespace-cdn.com/content/v1/51186ac8e4b085e20f8188a9/1389035383325-CUFR2S9SBV26SWILA1KI/ke17ZwdGBToddI8pDm48kOggE0Ch6pMGalwtLMqzsSB7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z5QPOohDIaIeljMHgDF5CVlOqpeNLcJ80NK65_fV7S1Ufo5RWkg_J4of0jUNHaDHx6pZKBvpVYzidBWCapg0tuoMuEaB2HPGSYDV-11UTcW2g/Beat+Drop+Push+Event-7.jpg",
      address: "615 11 Ave SE, Calgary, AB T2G 0B6",
      contactEmail: "beatdrop@beatdrop.ca"
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address
    };

    // meetups.push(newMeetup); // DOES NOT WORK!
    meetups = [newMeetup, ...meetups];
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      type="text"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="imageUrl"
      label="Image URL"
      type="text"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="email"
      label="E-Mail"
      type="email"
      value={email}
      on:input={event => (email = event.target.value)} />
    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      on:input={event => (description = event.target.value)} />
    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} />
</main>

```

## A Meet Up Item

```svelte
<script>
  import Button from "../UI/Button.svelte";

  export let title;
  export let subtitle;
  export let imageUrl;
  export let description;
  export let address;
  export let email;
</script>

<style>
  article {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 5px;
    background: white;
    margin: 1rem;
  }

  header,
  .content,
  footer {
    padding: 1rem;
  }

  .image {
    width: 100%;
    height: 14rem;
  }

  .image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  h1 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
    font-family: "Roboto Slab", sans-serif;
  }

  h1.is-favorite {
    background: #01a129;
    color: white;
    padding: 0 0.5rem;
    border-radius: 5px;
  }

  h2 {
    font-size: 1rem;
    color: #808080;
    margin: 0.5rem 0;
  }

  p {
    font-size: 1.25rem;
    margin: 0;
  }

  div {
    text-align: right;
  }

  .content {
    height: 4rem;
  }
</style>

<article>
  <header>
    <h1>{title}</h1>
    <h2>{subtitle}</h2>
    <p>{address}</p>
  </header>
  <div class="image">
    <img src={imageUrl} alt={title} />
  </div>
  <div class="content">
    <p>{description}</p>
  </div>
  <footer>
    <Button href="mailto:{email}" caption="Contact" />
    <Button mode="outline" type="button" caption="Favorite" />
    <Button type="button" caption="Show Details" />
  </footer>
</article>

```