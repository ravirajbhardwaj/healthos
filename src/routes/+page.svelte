<script lang="ts">
	import { cn } from '$lib/utils';
	import GridPattern from '$lib/components/magic/grid-pattern/grid-pattern.svelte';
	import * as Card from '$lib/components/ui/card';

	import {
		Timer,
		Dumbbell,
		Flame,
		Drumstick,
		Wheat,
		Droplets,
		Moon,
		Zap,
		Target,
		TrendingUp,
		CheckCircle2
	} from '@lucide/svelte';
	import { enhance } from '$app/forms';

	let { form } = $props();

	let email = $state('');
	let loading = $state(false);
	let sent = $state(false);

	const sections = [
		{
			title: 'The System',
			icon: Target,
			color: 'amber',
			items: [
				{ label: 'One formula', value: '3 pillars', icon: Zap, color: 'text-amber-500' },
				{ label: 'Auto plan', value: 'by goal', icon: Target, color: 'text-amber-500' },
				{ label: 'Daily habits', value: '3 only', icon: CheckCircle2, color: 'text-amber-500' }
			]
		},
		{
			title: 'Exercise & Sleep',
			icon: Timer,
			color: 'blue',
			items: [
				{ label: 'Workout Time', value: '45 min', icon: Timer, color: 'text-emerald-500' },
				{ label: 'Exercises', value: '10', icon: Dumbbell, color: 'text-purple-500' },
				{ divider: true },
				{ label: 'Duration', value: '7h 20m', icon: Moon, color: 'text-indigo-500' },
				{ label: 'Quality', value: '88%', icon: Zap, color: 'text-yellow-500' }
			]
		},
		{
			title: 'Diet',
			icon: Drumstick,
			color: 'rose',
			items: [
				{ label: 'Calories', value: '2230', icon: Flame, color: 'text-orange-500' },
				{ label: 'Carbs', value: '300g', icon: Wheat, color: 'text-amber-500' },
				{ label: 'Protein', value: '83g', icon: Drumstick, color: 'text-rose-500' },
				{ label: 'Fats', value: '55g', icon: Droplets, color: 'text-cyan-500' }
			]
		},
		{
			title: 'Progress',
			icon: TrendingUp,
			color: 'emerald',
			items: [
				{ label: 'Streak', value: '14 days', icon: Flame, color: 'text-orange-600' },
				{ label: 'Quality', value: '82%', icon: Moon, color: 'text-indigo-400' },
				{ label: 'Perfect', value: '💚 9', icon: CheckCircle2, color: 'text-emerald-500' }
			]
		}
	];

	const colorMap: Record<string, string> = {
		amber: 'bg-amber-50   text-amber-500   dark:bg-amber-950/30',
		rose: 'bg-rose-50    text-rose-500    dark:bg-rose-950/30',
		blue: 'bg-blue-50    text-blue-500    dark:bg-blue-950/30',
		emerald: 'bg-emerald-50 text-emerald-500 dark:bg-emerald-950/30'
	};

	const floatingLabels = [
		{
			label: 'Simple System',
			icon: Zap,
			pos: 'top-0 left-[-160px]',
			rotate: '-rotate-12',
			color:
				'border-green-500  bg-green-50  text-green-600  dark:bg-green-900/30  dark:text-green-400'
		},
		{
			label: 'Build YourSelf',
			icon: Dumbbell,
			pos: 'top-24 left-[-180px]',
			rotate: '-rotate-12',
			color:
				'border-yellow-500 bg-yellow-50 text-yellow-600 dark:bg-yellow-900/30 dark:text-yellow-400'
		},
		{
			label: 'Gamified Streaks',
			icon: Flame,
			pos: 'top-0 right-[-160px]',
			rotate: 'rotate-12',
			color:
				'border-teal-500   bg-teal-50   text-teal-600   dark:bg-teal-900/30   dark:text-teal-400'
		},
		{
			label: 'Track Progress',
			icon: TrendingUp,
			pos: 'top-24 right-[-180px]',
			rotate: 'rotate-12',
			color:
				'border-orange-500 bg-orange-50 text-orange-600 dark:bg-orange-900/30 dark:text-orange-400'
		}
	];
	import { MetaTags } from 'svelte-meta-tags';
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

		<!-- Hero -->
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
					<!-- Floating labels — desktop only -->
					{#each floatingLabels as fl (fl.label)}
						<div
							class="absolute {fl.pos} {fl.rotate} hidden items-center gap-1 rounded-sm border-b border-dashed lg:flex {fl.color} px-2 py-0.5 text-xs font-medium whitespace-nowrap"
						>
							<fl.icon class="h-3 w-3" />
							{fl.label}
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

				<!-- Mobile feature pills — visible only on mobile -->
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
							<button
								class="mt-4 text-sm font-medium text-emerald-600 hover:text-emerald-500 dark:text-emerald-400 dark:hover:text-emerald-300"
								onclick={() => {
									sent = false;
									email = '';
								}}
							>
								Use a different email
							</button>
						</div>
					{:else}
						<form
							method="POST"
							action="?/sendLink"
							use:enhance={() => {
								loading = true;
								return async ({ result, update }) => {
									loading = false;
									if (result.type === 'success') {
										sent = true;
									} else {
										update();
									}
								};
							}}
							class="relative flex w-full max-w-md items-center rounded-full border border-zinc-200 bg-white p-1.5 shadow-2xl transition-all focus-within:ring-1 focus-within:ring-zinc-300 dark:border-zinc-800 dark:bg-zinc-950 dark:focus-within:ring-zinc-700"
						>
							<input
								type="email"
								name="email"
								bind:value={email}
								placeholder="Enter your email to sign in or join..."
								required
								class="min-w-0 flex-1 border-0 bg-transparent px-4 text-sm outline-none focus:ring-0 focus:outline-none md:px-6"
								disabled={loading}
							/>
							<button
								type="submit"
								disabled={loading}
								class="group flex shrink-0 items-center gap-2 rounded-full bg-zinc-900 px-4 py-2.5 text-sm font-bold text-white transition-all hover:bg-emerald-600 active:scale-95 disabled:opacity-70 md:px-6 dark:bg-zinc-100 dark:text-black dark:hover:bg-emerald-400"
							>
								{#if loading}
									Sending...
								{:else}
									Join Now
									<Zap
										class="h-3.5 w-3.5 fill-current transition-transform group-hover:rotate-12"
									/>
								{/if}
							</button>
						</form>

						{#if form?.error}
							<p class="text-sm font-medium text-red-500">
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
						<span>
							Join <span class="font-bold text-zinc-900 dark:text-zinc-200">2,400+</span> others already
							in.
						</span>
					</div>
				</div>
			</div>

			<!-- Cards — centered under title -->
			<div class="mx-auto my-4 grid max-w-5xl grid-cols-1 gap-4 sm:grid-cols-2 lg:grid-cols-4">
				{#each sections as { title, icon: Icon, color, items } (title)}
					<Card.Root
						class="border-zinc-200 bg-white/50 opacity-75 backdrop-blur-sm dark:border-zinc-800 dark:bg-zinc-950/50"
					>
						<Card.Header class="pb-1">
							<Card.Title class="flex items-center gap-3 text-base font-bold md:text-lg">
								<div class="{colorMap[color]} rounded-xl p-2">
									<Icon size={18} />
								</div>
								{title}
							</Card.Title>
						</Card.Header>
						<Card.Content class="grid grid-cols-1 gap-x-3">
							{#each items as item (item)}
								{@render stat(item)}
							{/each}
						</Card.Content>
					</Card.Root>
				{/each}
			</div>
		</section>
	</main>
</div>
