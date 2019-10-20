<script>
  import Header from "./UI/Header.svelte";
  import FakeupGrid from "./Fakeups/FakeupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let imageUrl = "";
  let contactEmail = "";
  let description = "";

  let fakeups = [
    {
      id: "f1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup, we will have some experts that teach you how to code!",
      imageUrl:
        "https://images.unsplash.com/photo-1515879218367-8466d910aaa4?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "code@test.com"
    },
    {
      id: "f2",
      title: "Swit Together",
      subtitle: "Let's go for some swimming",
      description: "We will simply swim some rounds",
      imageUrl:
        "https://images.unsplash.com/photo-1519315901367-f34ff9154487?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1050&q=80",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "swim@test.com"
    }
  ];

  function addFakeup() {
    const newFakeup = {
      id: Math.random().toString(),
      title,
      subtitle,
      address,
      imageUrl,
      contactEmail,
      description
    };

    fakeups = [newFakeup, ...fakeups];
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
  <form on:submit|preventDefault={addFakeup}>
    <TextInput
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)}
      type="text" />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)}
      type="text" />
    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)}
      type="text" />
    <TextInput
      id="imageUrl"
      label="Image URL"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)}
      type="text" />
    <TextInput
      id="contactEmail"
      label="Email"
      value={contactEmail}
      on:input={event => (contactEmail = event.target.value)}
      type="email" />
    <TextInput
      id="description"
      label="Description"
      value={description}
      on:input={event => (description = event.target.value)}
      controlType="textarea"
      rows="3" />

    <Button type="submit" caption="Save" />
  </form>
  <FakeupGrid {fakeups} />
</main>
