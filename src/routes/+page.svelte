<script lang="ts">
	import { cn } from '$lib/utils';
	import GridPattern from '$lib/components/magic/grid-pattern/grid-pattern.svelte';
	import {
		Timer,
		Dumbbell,
		Droplet,
		Flame,
		Moon,
		Zap,
		Target,
		TrendingUp,
		CheckCircle2
	} from '@lucide/svelte';
	import { enhance } from '$app/forms';
	import { Input } from '$lib/components/ui/input';
	import { Button } from '$lib/components/ui/button';
	import { MetaTags } from 'svelte-meta-tags';
	import Stats from '$lib/components/Stats.svelte';

	let { form }: { form?: { error?: string } } = $props();

	let email = $state('');
	let loading = $state(false);
	let sent = $state(false);

	const floatingLabels = [
		{
			label: 'Simple System',
			icon: Zap,
			pos: 'top-4 left-[-210px]',
			rotate: '-rotate-6',
			color:
				'border-green-500/40 bg-green-500/10 text-green-700 dark:bg-green-950/60 dark:text-green-300',
			points: [
				{ icon: Droplet, text: 'One formula' },
				{ icon: CheckCircle2, text: '3 daily habits' }
			]
		},
		{
			label: 'Build YourSelf',
			icon: Dumbbell,
			pos: 'top-32 left-[-195px]',
			rotate: '-rotate-3',
			color:
				'border-yellow-500/40 bg-yellow-500/10 text-yellow-700 dark:bg-yellow-950/60 dark:text-yellow-300',
			points: [
				{ icon: Timer, text: '45 min workout' },
				{ icon: Dumbbell, text: 'Track strength' }
			]
		},
		{
			label: 'Gamified Streaks',
			icon: Flame,
			pos: 'top-4 right-[-210px]',
			rotate: 'rotate-12',
			color:
				'border-teal-500/40 bg-teal-500/10 text-teal-700 dark:bg-teal-950/60 dark:text-teal-300',
			points: [
				{ icon: Flame, text: 'Daily streaks' },
				{ icon: CheckCircle2, text: 'Perfect day badge' }
			]
		},
		{
			label: 'Track Progress',
			icon: TrendingUp,
			pos: 'top-32 right-[-195px]',
			rotate: 'rotate-12',
			color:
				'border-orange-500/40 bg-orange-500/10 text-orange-700 dark:bg-orange-950/60 dark:text-orange-300',
			points: [
				{ icon: Moon, text: 'Quality' },
				{ icon: Target, text: 'Goal tracking' }
			]
		}
	];
</script>

<MetaTags
	title="Health Algorithms"
	description="Health Algorithms = Exercise + Diet + Sleep, Stay Healthy with simple system."
	keywords={[
		'health',
		'exercise',
		'diet',
		'sleep',
		'health algorithms',
		'healthy',
		'healthy lifestyle'
	]}
/>
<!-- eslint-disable-next-line -->
{#snippet stat(item: any)}
	{#if item.divider}
		<div class="my-2 border-t border-zinc-100 dark:border-zinc-800"></div>
	{:else}
		<div class="flex items-center gap-2 py-1.5 text-sm">
			<item.icon class="h-4 w-4 {item.color} shrink-0" />
			<span class="text-zinc-600 dark:text-zinc-400">{item.label}</span>
			<span class="ml-auto font-bold text-zinc-900 dark:text-white">{item.value}</span>
		</div>
	{/if}
{/snippet}

<div class="h-screen w-full">
	<main class="relative w-full overflow-x-hidden">
		<GridPattern
			width={45}
			height={45}
			strokeDashArray="4 2"
			class={cn('mask-[radial-gradient(800px_circle_at_top_center,white,transparent)]')}
		/>

		<section class="relative z-10 w-full px-4 pt-2 pb-2 md:px-6 md:pt-4">
			<div class="mx-auto max-w-3xl text-center">
				<!-- Formula badge -->
				<div
					class="mx-auto mb-8 flex w-fit items-center gap-1.5 rounded-full border bg-muted/50 px-4 py-1.5 text-xs font-medium shadow-sm backdrop-blur-md md:text-sm dark:border-white/5 dark:bg-muted/20"
				>
					<span class="text-[#22C55E]">Health</span> =
					<span class="text-[#F97316]">Exercise</span> +
					<span class="text-[#EAB308]">Diet</span> +
					<span class="text-[#3B82F6]">Sleep</span>
				</div>

				<!-- Title + floating labels -->
				<div class="relative mx-auto w-fit">
					{#each floatingLabels as fl (fl.label)}
						<div
							class="absolute {fl.pos} {fl.rotate} hidden flex-col gap-1.5 rounded-xl border lg:flex {fl.color} min-w-40 px-3 py-2.5 text-xs font-medium whitespace-nowrap"
						>
							<div class="flex items-center gap-1">
								<fl.icon class="h-3 w-3" />
								{fl.label}
							</div>
							<div class="border-t border-current opacity-20"></div>
							{#each fl.points as point (point)}
								<div class="flex items-center gap-1.5 text-[11px] opacity-80">
									<point.icon class="h-3 w-3 shrink-0" />
									<span>{point.text}</span>
								</div>
							{/each}
						</div>
					{/each}

					<h1
						class="bg-linear-to-b from-zinc-900 to-zinc-600 bg-clip-text text-6xl font-bold tracking-tight text-transparent md:text-8xl dark:from-white dark:to-zinc-500"
					>
						Health OS
					</h1>
				</div>

				<p class="mx-auto mt-4 max-w-xl px-4 text-base text-muted-foreground md:px-0 md:text-lg">
					Track them. Improve them. Stay consistent.
				</p>

				<!-- Mobile feature pills -->
				<div class="mt-4 flex flex-wrap justify-center gap-2 lg:hidden">
					{#each floatingLabels as fl (fl.label)}
						<span
							class="flex items-center gap-1 rounded-full border px-3 py-1 text-xs font-medium {fl.color}"
						>
							<fl.icon class="h-3 w-3" />
							{fl.label}
						</span>
					{/each}
				</div>

				<!-- Email form -->
				<div class="mt-8 flex flex-col items-center gap-4">
					{#if sent}
						<div
							class="flex w-full max-w-md flex-col items-center justify-center rounded-2xl border border-green-500/20 bg-white p-6 text-center shadow-xl dark:border-green-500/10 dark:bg-zinc-950"
						>
							<div
								class="mb-3 flex h-12 w-12 items-center justify-center rounded-full bg-green-100 dark:bg-green-900/40"
							>
								<CheckCircle2 class="h-6 w-6 text-green-600 dark:text-green-400" />
							</div>
							<h3 class="text-lg font-bold text-zinc-900 dark:text-white">Check your email</h3>
							<p class="mt-2 text-sm text-zinc-600 dark:text-zinc-400">
								We sent a magic link to <strong>{email}</strong>.<br />Click it to sign in. Expires
								in 15 minutes.
							</p>
							<Button
								variant="link"
								class="mt-2 text-emerald-600 dark:text-emerald-400"
								onclick={() => {
									sent = false;
									email = '';
								}}
							>
								Use a different email
							</Button>
						</div>
					{:else}
						<form
							method="POST"
							action="?/sendLink"
							use:enhance={() => {
								loading = true;
								return async ({ result, update }) => {
									loading = false;
									if (result.type === 'success') sent = true;
									else update();
								};
							}}
							class="flex w-full max-w-md gap-2"
						>
							<Input
								type="email"
								name="email"
								bind:value={email}
								placeholder="Enter your email to sign in or join..."
								required
								disabled={loading}
								class="flex-1"
							/>
							<Button type="submit" disabled={loading}>
								{#if loading}
									Sending...
								{:else}
									Join Now <Zap class="ml-1 h-3.5 w-3.5 fill-current" />
								{/if}
							</Button>
						</form>
						<!-- eslint-disable-next-line -->
						{#if form?.error}
							<p class="text-sm font-medium text-destructive">
								{form.error === 'expired'
									? 'Link expired. Request a new one.'
									: 'Something went wrong. Please try again.'}
							</p>
						{/if}
					{/if}

					<!-- Social proof -->
					<div class="flex items-center gap-2 text-[11px] font-medium text-zinc-500">
						<div class="flex -space-x-2">
							<div
								class="h-5 w-5 rounded-full border-2 border-white bg-emerald-500 dark:border-zinc-900"
							></div>
							<div
								class="h-5 w-5 rounded-full border-2 border-white bg-cyan-500 dark:border-zinc-900"
							></div>
							<div
								class="h-5 w-5 rounded-full border-2 border-white bg-orange-500 dark:border-zinc-900"
							></div>
						</div>
						<span
							>Join <span class="font-bold text-zinc-900 dark:text-zinc-200">2,400+</span> others already
							in.</span
						>
					</div>
				</div>
			</div>

			<Stats />
		</section>
	</main>
</div>
