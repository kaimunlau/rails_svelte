<script>
	import { Button } from "$lib/components/ui/button/index.js";
	import * as Card from "$lib/components/ui/card/index.js";
	import { Input } from "$lib/components/ui/input/index.js";
	import { InputError } from "$lib/components/ui/input-error/index.js";
	import { Label } from "$lib/components/ui/label/index.js";
	import { Link, useForm } from "@inertiajs/svelte";

  const form = useForm({
    email_address: "m@mail.com",
    password: "secret",
    password_confirmation: "secret",
  })

  function submit(e) {
    e.preventDefault()
    $form.post('/signup')
  }
</script>

<Card.Root class="mx-auto max-w-sm w-full">
	<Card.Header>
		<Card.Title class="text-2xl">Sign up</Card.Title>
		<Card.Description>Enter your email to create an account</Card.Description>
	</Card.Header>
	<Card.Content>
		<form onsubmit={submit}>
			<div class="grid gap-4">
				<div class="grid gap-2">
					<Label for="email_address">Email</Label>
					<Input id="email_address" type="email" placeholder="m@example.com" required bind:value={$form.email_address} />
					<InputError>{$form.errors.email_address}</InputError>
				</div>
				<div class="grid gap-2">
					<Label for="password">Password</Label>
					<Input id="password" type="password" required bind:value={$form.password}/>
					<InputError>{$form.errors.password}</InputError>
				</div>
        <div class="grid gap-2">
					<Label for="password_confirmation">Password Confirmation</Label>
					<Input id="password_confirmation" type="password" required bind:value={$form.password_confirmation}/>
					<InputError>{$form.errors.password_confirmation}</InputError>
				</div>
				<Button type="submit" class="w-full">Sign up</Button>
			</div>
			<div class="mt-4 text-center text-sm">
				Already have an account?
				<Link href="/login" class="underline"> Log in </Link>
			</div>
		</form>
	</Card.Content>
</Card.Root>
