<script lang="ts">
    import { onMount } from 'svelte';
    import experiencesData from '../../util/experiences.json';
  
    // Define a type for the experience data
    export interface Experience {
      company: string;
      position: string;
      startDate: string;
      endDate: string;
      description: string;
      companyIcon?: string;
    }
  
    let experiences: Experience[] = [];
  
    onMount(() => {
      // Use the experiences data from the imported JSON file
      experiences = experiencesData;
    });

    function companyIconExists(iconPath: string | undefined): boolean {
    return !!iconPath;
  }
  </script>
  
  <section class="wrapper" id="experiences">
    <div class="title">
      <h2><span>code:</span>experiences</h2>
    </div>
    <div class="grid">
      {#each experiences as { company, companyIcon, position, startDate, endDate, description }}
        <div class="experience-card">
          <div class="info">
            {#if companyIconExists(companyIcon)}
            <img src={`/experiences/${companyIcon}`} alt={`${company} icon`} class="company-icon" />
          {/if}
            <h6>{company} - </h6>
            <h6>{position}</h6>
          </div>
          <div>
            <h6>{startDate} - {endDate}</h6>
          </div>
          <div>
            <h6>{description}</h6>
          </div>
        </div>
      {/each}
    </div>
  </section>
  
  <style lang="scss">
	@import '../../styles/mixins.scss';

	.title {
		display: flex;
		justify-content: center;
		margin-top: 0;

		@media (max-width: 868px) {
			justify-content: left;
		}
	}
    .experience-card {
    padding: 1rem 1.25rem;
    background-color: var(--neutral-two);
    border-radius: 8px;
    min-height: 140px;
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    transition: transform 0.3s var(--bezier-one), box-shadow 0.3s var(--bezier-one);
    justify-content: space-between;
    backdrop-filter: blur(5px);
    -webkit-backdrop-filter: blur(5px);
    background-blend-mode: overlay;
    border: 1px solid var(--neutral-four);

    &:hover {
      transform: translateY(-2px);
      box-shadow: 0px 15px 25px -10px rgba(0, 0, 0, 0.25);
    }
  }

  .company-icon {
    height: 24px; /* Adjust the height as needed */
    width: auto;
    margin-right: 8px;
  }

	.shimmer {
		animation-duration: 2.2s;
		animation-fill-mode: forwards;
		animation-iteration-count: infinite;
		animation-name: shimmer;
		animation-timing-function: linear;
		background: #ddd;
		background: linear-gradient(
			to right,
			var(--neutral-two) 8%,
			var(--neutral-one) 18%,
			var(--neutral-two) 33%
		);
		background-size: 1200px 100%;
	}

	@keyframes shimmer {
		0% {
			background-position: -1200px 0;
		}
		100% {
			background-position: 1200px 0;
		}
	}

	a {
		text-decoration: none;
		color: var(--white);
		height: 100%;
		border-radius: 8px;
	}

	img {
		height: 16px;
		width: auto;
	}

	h2 {
		display: inline-block;
		margin-bottom: 1rem;
	}

	#star {
		transform: translateY(-1px);
	}

	#fork {
		height: 17px;
	}

	#pfp {
		border-radius: 50%;
		height: 16px;
	}

	#top-part {
		display: flex;
		justify-content: space-between;
	}

	#open {
		height: 20px;
		transition: filter 0.3s var(--bezier-one);
	}

	span {
		color: var(--yellow);
	}

	.grid {
		gap: 0.8rem;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		display: grid;
		grid-template-columns: 1fr 1fr;
		margin-bottom: 3rem;
		position: relative;

		&:before {
			@include outlineText($content: '¤', $translateX: 1010%, $translateY: -30%);
		}

		@media (max-width: 600px) {
			grid-template-columns: 1fr;
		}

		@media (max-width: 868px) {
			margin-bottom: 2rem;
		}
	}

	.dot {
		height: 11px;
		width: 11px;
		border-radius: 50%;
		display: inline-block;
	}

	.info {
		display: flex;
		gap: 0.2rem;
		align-items: center;

		&-container {
			display: flex;
			gap: 0.9rem;
		}
	}
    img {
        border-radius: 100px;
    }
</style>