<script>
  export let project;
  const { logo, alt, title, githubUrl } = project;
</script>

<style lang="scss">
  .project {
    display: flex;
    justify-content: space-between;
    padding: 0.625rem var(--micro);
    background: var(--off-white);
    border-radius: 1.25rem;
    transition: all 0.2s;

    @media (max-width: 454px) {
      padding: var(--macro) var(--micro);
    }

    &__left {
      display: flex;
      place-items: center;
    }

    &__logo {
      height: 2.25rem;
      width: 2.25rem;
      margin-right: var(--micro);
      filter: grayscale(100%) opacity(0.5);
      -webkit-filter: grayscale(100%) opacity(0.5);
      transition: all 0.2s;

      @media (max-width: 454px) {
        width: 25px;
        margin-right: var(--macro);
      }
    }

    h5 {
      color: var(--dark-grey);
      transition: all 0.2s;
    }

    &:not(:last-child) {
      margin-bottom: var(--micro);
    }

    &:hover,
    &:focus {
      background: var(--brand-light);

      .project__logo {
        filter: grayscale(0) opacity(1);
        -webkit-filter: grayscale(0) opacity(1);
      }

      h5 {
        color: var(--black);
      }

      .btn-tertiary {
        opacity: 1;
      }
    }
  }

  .btn-tertiary {
    max-width: 9rem;
    padding-left: 0.75rem;
    padding-right: 0.75rem;
    opacity: 0;

    @media (max-width: 500px) {
      display: none;
    }
  }
</style>

<a href={`https://gitpod.io#${githubUrl}`} target="_blank" class="project">
  <div class="project__left">
    <img src={`/${logo}`} {alt} class="project__logo" width="36" height="36" />
    <h5>{title}</h5>
  </div>
  <span class="btn-tertiary">Launch workspace</span>
</a>
