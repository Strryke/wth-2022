<template>
  <div class="usp-container">
    <div class="usp-children">
      <!-- <font-awesome-icon icon="fa-solid fa-user-secret" /> -->
      <font-awesome-icon class="fa-icon" icon="fa-solid fa-sack-dollar" />
      <div>
        <div class="title">$3000 Prize Pool</div>
        <!-- <div class="subtitle">Child</div> -->
      </div>
    </div>
    <div class="usp-children">
      <!-- <font-awesome-icon class="fa-icon" icon="fa-solid fa-user-secret" /> -->
      <font-awesome-icon class="fa-icon" icon="fa-solid fa-thumbs-up" />
      <div>
        <div class="title">Completely Free</div>
        <!-- <div class="subtitle">Child</div> -->
      </div>
    </div>
    <div class="usp-children">
      <!-- <font-awesome-icon class="fa-icon" icon="fa-solid fa-user-secret" /> -->
      <font-awesome-icon class="fa-icon" icon="fa-solid fa-users" />
      <div>
        <div class="title">All Skill Levels Welcome!</div>
        <!-- <div class="subtitle">Child</div> -->
      </div>
    </div>
  </div>
</template>

<style scoped>
/* triple column grid layout */
.usp-container {
  background-color: var(--slope-body-color);
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
  margin: 0 auto;
  padding: 100px calc(10vw + 20px);
}

@media screen and (max-width: 768px) {
  .usp-container {
    grid-template-columns: repeat(1, 1fr);
  }
}

.fa-icon {
  font-size: clamp(2rem, 2vw, 3rem);
  color: var(--color-section-title-text);
  padding-right: 15px;
}

.usp-children {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin: auto;
}

.title {
  font-family: var(--font-primary);
  font-size: clamp(1rem, 2vw, 2rem);
}

.subtitle {
  font-family: var(--font-secondary), sans-serif;
  font-size: 30px;
  font-weight: 500;
}
</style>
