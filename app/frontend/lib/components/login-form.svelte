<script>
	import { Button } from "$lib/components/ui/button/index.js";
	import * as Card from "$lib/components/ui/card/index.js";
	import { Input } from "$lib/components/ui/input/index.js";
	import { InputError } from "$lib/components/ui/input-error/index.js";
	import { Label } from "$lib/components/ui/label/index.js";
	import { Link, useForm } from "@inertiajs/svelte";

  const form = useForm({
    email_address: null,
    password: null,
  })

  function submit(e) {
    e.preventDefault()
    $form.post('/login')
  }
</script>

<Card.Root class="mx-auto max-w-sm w-full">
	<Card.Header>
		<Card.Title class="text-2xl">Log in</Card.Title>
		<Card.Description>Enter your email below to login to your account</Card.Description>
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
					<div class="flex items-center">
						<Label for="password">Password</Label>
						<Link href="/forgot-password" class="ml-auto inline-block text-sm underline"> Forgot your password? </Link>
					</div>
					<Input id="password" type="password" required bind:value={$form.password}/>
					<InputError>{$form.errors.password}</InputError>
				</div>
				<Button type="submit" class="w-full">Log in</Button>
			</div>
			<div class="mt-4 text-center text-sm">
				Don't have an account?
				<Link href="/signup" class="underline"> Sign up </Link>
			</div>
		</form>
	</Card.Content>
</Card.Root>
