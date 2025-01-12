<script lang="ts">
	import { writable } from 'svelte/store';
	import emailjs from '@emailjs/browser';

	const isModalOpen = writable(false);
	const modalMessage = writable('');

	// EmailJS Configuration
	const sendEmail = (e: Event) => {
		const form = e.target as HTMLFormElement;

		emailjs
			.sendForm('service_1e7vy6s', 'template_k3f65qt', form, {
				publicKey: 'sqOJqdqwLgGUfoHVC'
			})
			.then(
				() => {
					modalMessage.set('Thanks! Your message was sent successfully.');
					isModalOpen.set(true);
					// Clear the form
					form.reset();
				},
				(error) => {
					console.error('FAILED...', error.text);
					modalMessage.set('Failed to send your message. Please try again.');
					isModalOpen.set(true);
				}
			);
	};

	const closeModal = () => {
		isModalOpen.set(false);
	};
</script>

<div class="card shadow-lg flex max-w-3xl items-center justify-center mx-4 sm:mx-auto">
	<div class="p-8">
		<h2 class="mb-6 text-center">
			Let's connect! Fill out the form below, and I'll get back to you as soon as possible.
		</h2>
		<form on:submit|preventDefault={sendEmail}>
			<div class="mb-4">
				<label class="label">
					<input
						class="input"
						title="Input (text)"
						type="text"
						name="user_name"
						placeholder="Name"
						required
					/>
				</label>
			</div>
			<div class="mb-4">
				<label class="label">
					<input
						class="input"
						title="Input (text)"
						type="email"
						name="user_email"
						placeholder="Email"
						required
					/>
				</label>
			</div>
			<div class="mb-4">
				<label class="label">
					<textarea
						class="textarea"
						rows="4"
						name="message"
						placeholder="Your message here..."
						required
					></textarea>
				</label>
			</div>
			<div>
				<div class="flex justify-center">
					<button type="submit" class="btn btn-md variant-filled-primary py-2 px-10">
						Submit
					</button>
				</div>
			</div>
		</form>
	</div>
</div>

<!-- Modal -->
{#if $isModalOpen}
	<div class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50 z-50">
		<div class="card shadow-lg p-6 max-w-md w-full">
			<p class="text-center text-lg">{$modalMessage}</p>
			<div class="flex justify-center mt-4">
				<button on:click={closeModal} class="btn btn-md variant-filled-primary py-2 px-6">
					OK
				</button>
			</div>
		</div>
	</div>
{/if}

<style>
</style>
