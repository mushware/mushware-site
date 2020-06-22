<template>
  <form name="contact" method="POST" netlify-honeypot="comment" data-netlify="true" data-netlify-recaptcha="true">
    <input type="hidden" name="form-name" value="contact">
    <!-- Name -->
    <div class="field">
      <label class="label is-medium">Name</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          name="name"
          type="text"
          placeholder="John Smith"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="user" />
        </span>
      </div>
    </div>
    <!-- Email -->
    <div class="field">
      <label class="label is-medium">Email</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          name="email"
          type="email"
          placeholder="you@email.com"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="envelope" />
        </span>
      </div>
    </div>
    <!-- Subject -->
    <div class="field">
      <label class="label is-medium">Subject</label>
      <div class="control has-icons-left">
        <input
          class="input is-medium"
          name="subject"
          type="text"
          placeholder="Brief Summary"
        />
        <span class="icon is-small is-left">
          <font-awesome-icon icon="briefcase" />
        </span>
      </div>
    </div>
    <!-- Message -->
    <div class="field">
      <label class="label is-medium">Message</label>
      <div class="control">
        <textarea
          class="textarea"
          name="message"
          placeholder="Your message..."
          rows="8"
        ></textarea>
      </div>
    </div>
    <!-- File -->
    <div class="field">
      <label class="label is-medium">Message</label>
      <div class="control">
        <input
          class="input is-medium"
          name="file"
          type="file"
          placeholder="Attach file if required (and less than 1MB)"
        />
      </div>
    </div>
    <p style="visibility:hidden">
      <label>Comment: 
        <input name="comment" />
      </label>
    </p>
    <div data-netlify-recaptcha="true"></div>
    <div class="control">
      <button class="button is-primary">
        Contact Us
      </button>
    </div>
  </form>
</template>
