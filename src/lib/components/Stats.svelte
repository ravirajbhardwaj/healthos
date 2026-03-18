<script lang="ts">
	type Food = {
		name: string;
		serving: string;
		cat: string;
		emoji: string;
		cal: number;
		protein: number;
		carbs: number;
		fat: number;
		cardLight: string;
		cardDark: string;
		border: string;
		textLight: string;
		textDark: string;
	};

	type Exercise = {
		name: string;
		cat: 'exercise';
		emoji: string;
		muscle: string; // primary muscle
		secondary: string; // secondary muscles
		sets: number;
		reps: string; // e.g. "8-12" or "15"
		rest: string; // e.g. "60s"
		level: 'Beginner' | 'Intermediate' | 'Advanced';
		cardLight: string;
		cardDark: string;
		border: string;
		textLight: string;
		textDark: string;
	};

	const foods: Food[] = [
		{
			name: 'Banana',
			serving: '1 medium (118g)',
			cat: 'fruit',
			emoji: '🍌',
			cal: 105,
			protein: 1.3,
			carbs: 27,
			fat: 0.4,
			cardLight: 'bg-yellow-500/10',
			cardDark: 'dark:bg-yellow-950/60',
			border: 'border-yellow-500/40',
			textLight: 'text-yellow-700',
			textDark: 'dark:text-yellow-300'
		},
		{
			name: 'Chicken Breast',
			serving: '100g cooked',
			cat: 'protein',
			emoji: '🍗',
			cal: 165,
			protein: 31,
			carbs: 0,
			fat: 3.6,
			cardLight: 'bg-orange-500/10',
			cardDark: 'dark:bg-orange-950/60',
			border: 'border-orange-500/40',
			textLight: 'text-orange-700',
			textDark: 'dark:text-orange-300'
		},
		{
			name: 'Brown Rice',
			serving: '1 cup cooked',
			cat: 'grain',
			emoji: '🍚',
			cal: 216,
			protein: 5,
			carbs: 45,
			fat: 1.8,
			cardLight: 'bg-green-500/10',
			cardDark: 'dark:bg-green-950/60',
			border: 'border-green-500/40',
			textLight: 'text-green-700',
			textDark: 'dark:text-green-300'
		},
		{
			name: 'Avocado',
			serving: '½ avocado (68g)',
			cat: 'fruit',
			emoji: '🥑',
			cal: 114,
			protein: 1.3,
			carbs: 6,
			fat: 10.5,
			cardLight: 'bg-lime-500/10',
			cardDark: 'dark:bg-lime-950/60',
			border: 'border-lime-500/40',
			textLight: 'text-lime-700',
			textDark: 'dark:text-lime-300'
		},
		{
			name: 'Egg',
			serving: '1 large',
			cat: 'protein',
			emoji: '🥚',
			cal: 78,
			protein: 6,
			carbs: 0.6,
			fat: 5,
			cardLight: 'bg-amber-500/10',
			cardDark: 'dark:bg-amber-950/60',
			border: 'border-amber-500/40',
			textLight: 'text-amber-700',
			textDark: 'dark:text-amber-300'
		},
		{
			name: 'Broccoli',
			serving: '1 cup (91g)',
			cat: 'vegetable',
			emoji: '🥦',
			cal: 31,
			protein: 2.6,
			carbs: 6,
			fat: 0.3,
			cardLight: 'bg-emerald-500/10',
			cardDark: 'dark:bg-emerald-950/60',
			border: 'border-emerald-500/40',
			textLight: 'text-emerald-700',
			textDark: 'dark:text-emerald-300'
		},
		{
			name: 'Greek Yogurt',
			serving: '170g',
			cat: 'dairy',
			emoji: '🥛',
			cal: 100,
			protein: 17,
			carbs: 6,
			fat: 0.7,
			cardLight: 'bg-sky-500/10',
			cardDark: 'dark:bg-sky-950/60',
			border: 'border-sky-500/40',
			textLight: 'text-sky-700',
			textDark: 'dark:text-sky-300'
		},
		{
			name: 'Salmon',
			serving: '100g cooked',
			cat: 'protein',
			emoji: '🐟',
			cal: 208,
			protein: 20,
			carbs: 0,
			fat: 13,
			cardLight: 'bg-rose-500/10',
			cardDark: 'dark:bg-rose-950/60',
			border: 'border-rose-500/40',
			textLight: 'text-rose-700',
			textDark: 'dark:text-rose-300'
		},
		{
			name: 'Sweet Potato',
			serving: '1 medium (130g)',
			cat: 'vegetable',
			emoji: '🍠',
			cal: 112,
			protein: 2,
			carbs: 26,
			fat: 0.1,
			cardLight: 'bg-orange-500/10',
			cardDark: 'dark:bg-orange-950/60',
			border: 'border-orange-500/40',
			textLight: 'text-orange-700',
			textDark: 'dark:text-orange-300'
		},
		{
			name: 'Oats',
			serving: '½ cup dry (40g)',
			cat: 'grain',
			emoji: '🌾',
			cal: 150,
			protein: 5,
			carbs: 27,
			fat: 2.5,
			cardLight: 'bg-yellow-500/10',
			cardDark: 'dark:bg-yellow-950/60',
			border: 'border-yellow-500/40',
			textLight: 'text-yellow-700',
			textDark: 'dark:text-yellow-300'
		},
		{
			name: 'Apple',
			serving: '1 medium (182g)',
			cat: 'fruit',
			emoji: '🍎',
			cal: 95,
			protein: 0.5,
			carbs: 25,
			fat: 0.3,
			cardLight: 'bg-red-500/10',
			cardDark: 'dark:bg-red-950/60',
			border: 'border-red-500/40',
			textLight: 'text-red-700',
			textDark: 'dark:text-red-300'
		},
		{
			name: 'Almonds',
			serving: '28g (23 nuts)',
			cat: 'protein',
			emoji: '🥜',
			cal: 164,
			protein: 6,
			carbs: 6,
			fat: 14,
			cardLight: 'bg-amber-500/10',
			cardDark: 'dark:bg-amber-950/60',
			border: 'border-amber-500/40',
			textLight: 'text-amber-700',
			textDark: 'dark:text-amber-300'
		},
		{
			name: 'Spinach',
			serving: '1 cup raw (30g)',
			cat: 'vegetable',
			emoji: '🌿',
			cal: 7,
			protein: 0.9,
			carbs: 1.1,
			fat: 0.1,
			cardLight: 'bg-green-500/10',
			cardDark: 'dark:bg-green-950/60',
			border: 'border-green-500/40',
			textLight: 'text-green-700',
			textDark: 'dark:text-green-300'
		},
		{
			name: 'Cottage Cheese',
			serving: '½ cup (113g)',
			cat: 'dairy',
			emoji: '🧀',
			cal: 90,
			protein: 12,
			carbs: 5,
			fat: 2.5,
			cardLight: 'bg-teal-500/10',
			cardDark: 'dark:bg-teal-950/60',
			border: 'border-teal-500/40',
			textLight: 'text-teal-700',
			textDark: 'dark:text-teal-300'
		},
		{
			name: 'Quinoa',
			serving: '1 cup cooked',
			cat: 'grain',
			emoji: '🌱',
			cal: 222,
			protein: 8,
			carbs: 39,
			fat: 3.5,
			cardLight: 'bg-emerald-500/10',
			cardDark: 'dark:bg-emerald-950/60',
			border: 'border-emerald-500/40',
			textLight: 'text-emerald-700',
			textDark: 'dark:text-emerald-300'
		},
		{
			name: 'Blueberries',
			serving: '1 cup (148g)',
			cat: 'fruit',
			emoji: '🫐',
			cal: 84,
			protein: 1.1,
			carbs: 21,
			fat: 0.5,
			cardLight: 'bg-violet-500/10',
			cardDark: 'dark:bg-violet-950/60',
			border: 'border-violet-500/40',
			textLight: 'text-violet-700',
			textDark: 'dark:text-violet-300'
		}
	];

	const exercises: Exercise[] = [
		{
			name: 'Push-up',
			cat: 'exercise',
			emoji: '💪',
			muscle: 'Chest',
			secondary: 'Triceps, Shoulders',
			sets: 3,
			reps: '12-15',
			rest: '45s',
			level: 'Beginner',
			cardLight: 'bg-blue-500/10',
			cardDark: 'dark:bg-blue-950/60',
			border: 'border-blue-500/40',
			textLight: 'text-blue-700',
			textDark: 'dark:text-blue-300'
		},
		{
			name: 'Pull-up',
			cat: 'exercise',
			emoji: '🏋️',
			muscle: 'Back',
			secondary: 'Biceps, Core',
			sets: 3,
			reps: '6-10',
			rest: '90s',
			level: 'Intermediate',
			cardLight: 'bg-indigo-500/10',
			cardDark: 'dark:bg-indigo-950/60',
			border: 'border-indigo-500/40',
			textLight: 'text-indigo-700',
			textDark: 'dark:text-indigo-300'
		},
		{
			name: 'Squat',
			cat: 'exercise',
			emoji: '🦵',
			muscle: 'Quads',
			secondary: 'Glutes, Hamstrings',
			sets: 4,
			reps: '10-12',
			rest: '60s',
			level: 'Beginner',
			cardLight: 'bg-purple-500/10',
			cardDark: 'dark:bg-purple-950/60',
			border: 'border-purple-500/40',
			textLight: 'text-purple-700',
			textDark: 'dark:text-purple-300'
		},
		{
			name: 'Deadlift',
			cat: 'exercise',
			emoji: '🏗️',
			muscle: 'Hamstrings',
			secondary: 'Back, Glutes',
			sets: 4,
			reps: '5-8',
			rest: '120s',
			level: 'Advanced',
			cardLight: 'bg-red-500/10',
			cardDark: 'dark:bg-red-950/60',
			border: 'border-red-500/40',
			textLight: 'text-red-700',
			textDark: 'dark:text-red-300'
		},
		{
			name: 'Plank',
			cat: 'exercise',
			emoji: '🧱',
			muscle: 'Core',
			secondary: 'Shoulders, Glutes',
			sets: 3,
			reps: '30-60s',
			rest: '30s',
			level: 'Beginner',
			cardLight: 'bg-teal-500/10',
			cardDark: 'dark:bg-teal-950/60',
			border: 'border-teal-500/40',
			textLight: 'text-teal-700',
			textDark: 'dark:text-teal-300'
		},
		{
			name: 'Bench Press',
			cat: 'exercise',
			emoji: '🔩',
			muscle: 'Chest',
			secondary: 'Triceps, Delts',
			sets: 4,
			reps: '8-10',
			rest: '90s',
			level: 'Intermediate',
			cardLight: 'bg-blue-500/10',
			cardDark: 'dark:bg-blue-950/60',
			border: 'border-blue-500/40',
			textLight: 'text-blue-700',
			textDark: 'dark:text-blue-300'
		},
		{
			name: 'Lunges',
			cat: 'exercise',
			emoji: '🚶',
			muscle: 'Quads',
			secondary: 'Glutes, Calves',
			sets: 3,
			reps: '10/leg',
			rest: '60s',
			level: 'Beginner',
			cardLight: 'bg-violet-500/10',
			cardDark: 'dark:bg-violet-950/60',
			border: 'border-violet-500/40',
			textLight: 'text-violet-700',
			textDark: 'dark:text-violet-300'
		},
		{
			name: 'Shoulder Press',
			cat: 'exercise',
			emoji: '🙌',
			muscle: 'Shoulders',
			secondary: 'Triceps, Traps',
			sets: 3,
			reps: '10-12',
			rest: '60s',
			level: 'Intermediate',
			cardLight: 'bg-cyan-500/10',
			cardDark: 'dark:bg-cyan-950/60',
			border: 'border-cyan-500/40',
			textLight: 'text-cyan-700',
			textDark: 'dark:text-cyan-300'
		},
		{
			name: 'Bicep Curl',
			cat: 'exercise',
			emoji: '💪',
			muscle: 'Biceps',
			secondary: 'Forearms',
			sets: 3,
			reps: '12-15',
			rest: '45s',
			level: 'Beginner',
			cardLight: 'bg-amber-500/10',
			cardDark: 'dark:bg-amber-950/60',
			border: 'border-amber-500/40',
			textLight: 'text-amber-700',
			textDark: 'dark:text-amber-300'
		},
		{
			name: 'Tricep Dip',
			cat: 'exercise',
			emoji: '🤸',
			muscle: 'Triceps',
			secondary: 'Chest, Shoulders',
			sets: 3,
			reps: '10-12',
			rest: '60s',
			level: 'Intermediate',
			cardLight: 'bg-rose-500/10',
			cardDark: 'dark:bg-rose-950/60',
			border: 'border-rose-500/40',
			textLight: 'text-rose-700',
			textDark: 'dark:text-rose-300'
		},
		{
			name: 'Romanian DL',
			cat: 'exercise',
			emoji: '🏋️',
			muscle: 'Hamstrings',
			secondary: 'Glutes, Lower Back',
			sets: 3,
			reps: '10-12',
			rest: '90s',
			level: 'Intermediate',
			cardLight: 'bg-orange-500/10',
			cardDark: 'dark:bg-orange-950/60',
			border: 'border-orange-500/40',
			textLight: 'text-orange-700',
			textDark: 'dark:text-orange-300'
		},
		{
			name: 'Mountain Climb',
			cat: 'exercise',
			emoji: '🧗',
			muscle: 'Core',
			secondary: 'Shoulders, Hip Flex',
			sets: 3,
			reps: '20/leg',
			rest: '30s',
			level: 'Beginner',
			cardLight: 'bg-emerald-500/10',
			cardDark: 'dark:bg-emerald-950/60',
			border: 'border-emerald-500/40',
			textLight: 'text-emerald-700',
			textDark: 'dark:text-emerald-300'
		},
		{
			name: 'Lat Pulldown',
			cat: 'exercise',
			emoji: '🔽',
			muscle: 'Lats',
			secondary: 'Biceps, Rhomboids',
			sets: 4,
			reps: '10-12',
			rest: '60s',
			level: 'Beginner',
			cardLight: 'bg-indigo-500/10',
			cardDark: 'dark:bg-indigo-950/60',
			border: 'border-indigo-500/40',
			textLight: 'text-indigo-700',
			textDark: 'dark:text-indigo-300'
		},
		{
			name: 'Calf Raise',
			cat: 'exercise',
			emoji: '🦶',
			muscle: 'Calves',
			secondary: 'Soleus',
			sets: 3,
			reps: '15-20',
			rest: '30s',
			level: 'Beginner',
			cardLight: 'bg-lime-500/10',
			cardDark: 'dark:bg-lime-950/60',
			border: 'border-lime-500/40',
			textLight: 'text-lime-700',
			textDark: 'dark:text-lime-300'
		},
		{
			name: 'Face Pull',
			cat: 'exercise',
			emoji: '🎯',
			muscle: 'Rear Delts',
			secondary: 'Traps, Rotator Cuff',
			sets: 3,
			reps: '15-20',
			rest: '45s',
			level: 'Intermediate',
			cardLight: 'bg-pink-500/10',
			cardDark: 'dark:bg-pink-950/60',
			border: 'border-pink-500/40',
			textLight: 'text-pink-700',
			textDark: 'dark:text-pink-300'
		},
		{
			name: 'Hip Thrust',
			cat: 'exercise',
			emoji: '🍑',
			muscle: 'Glutes',
			secondary: 'Hamstrings, Core',
			sets: 4,
			reps: '12-15',
			rest: '60s',
			level: 'Intermediate',
			cardLight: 'bg-purple-500/10',
			cardDark: 'dark:bg-purple-950/60',
			border: 'border-purple-500/40',
			textLight: 'text-purple-700',
			textDark: 'dark:text-purple-300'
		}
	];

	const levelColor: Record<string, string> = {
		Beginner: 'text-emerald-400',
		Intermediate: 'text-amber-400',
		Advanced: 'text-rose-400'
	};

	const categories = ['all', 'fruit', 'vegetable', 'grain', 'protein', 'dairy', 'exercise'];
	let activeCategory = $state('all');

	const isExerciseMode = $derived(activeCategory === 'exercise');

	const filteredFoods = $derived(
		activeCategory === 'all'
			? foods
			: activeCategory === 'exercise'
				? []
				: foods.filter((f) => f.cat === activeCategory)
	);

	function maxMacro(f: Food) {
		return Math.max(f.protein, f.carbs, f.fat, 1);
	}
	function pct(val: number, max: number) {
		return Math.round((val / max) * 100);
	}

	const barColors = { protein: '#4ade80', carbs: '#facc15', fat: '#f87171' };
</script>

<div class="my-10 w-full px-0">
	<!-- Filter chips -->
	<div class="mb-6 flex flex-wrap justify-center gap-2">
		{#each categories as cat (cat)}
			<button
				onclick={() => (activeCategory = cat)}
				class="rounded-full border px-3 py-1 text-xs font-medium capitalize transition-all
          {activeCategory === cat
					? 'border-transparent bg-foreground text-background'
					: 'border-border bg-transparent text-muted-foreground hover:border-foreground/40 hover:text-foreground'}"
			>
				{cat}
			</button>
		{/each}
	</div>

	<!-- ── FOOD CARDS ── -->
	{#if !isExerciseMode}
		<div class="grid grid-cols-2 gap-3 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5">
			{#each filteredFoods as food (food.name)}
				{@const mx = maxMacro(food)}
				<div
					class="group relative cursor-pointer overflow-hidden rounded-2xl border
                 {food.border} {food.cardLight} {food.cardDark}"
					style="aspect-ratio: 3/4;"
				>
					<!-- FRONT -->
					<div
						class="absolute inset-0 flex flex-col transition-opacity duration-300 group-hover:opacity-0"
					>
						<div class="flex flex-1 items-center justify-center pt-3 text-5xl">{food.emoji}</div>
						<div class="mx-3 border-t {food.border} opacity-40"></div>
						<div class="flex flex-col gap-0.5 px-3 py-2.5">
							<p
								class="truncate text-xs leading-tight font-semibold {food.textLight} {food.textDark}"
							>
								{food.name}
							</p>
							<p class="truncate text-[10px] {food.textLight} {food.textDark} opacity-60">
								{food.serving}
							</p>
							<div class="mt-1.5 flex items-center justify-between">
								<span class="text-[10px] {food.textLight} {food.textDark} capitalize opacity-50"
									>{food.cat}</span
								>
								<span class="text-[11px] font-bold {food.textLight} {food.textDark}"
									>{food.cal} kcal</span
								>
							</div>
						</div>
					</div>

					<!-- BACK -->
					<div
						class="absolute inset-0 flex flex-col justify-end rounded-2xl p-3 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
						style="background:rgba(9,9,11,0.90);backdrop-filter:blur(6px);"
					>
						<p class="mb-0.5 truncate text-[14px] font-semibold text-white">{food.name}</p>
						<p class="mb-3 truncate text-[10px] text-white/50">{food.serving}</p>
						<div class="mb-3 flex flex-col gap-2">
							{#each [{ label: 'Protein', val: food.protein, color: barColors.protein }, { label: 'Carbs', val: food.carbs, color: barColors.carbs }, { label: 'Fat', val: food.fat, color: barColors.fat }] as macro (macro.label)}
								<div>
									<div class="mb-1 flex justify-between">
										<span class="text-[10px] text-white/60">{macro.label}</span>
										<span class="text-[10px] font-medium text-white">{macro.val}g</span>
									</div>
									<div
										class="h-1.5 overflow-hidden rounded-full"
										style="background:rgba(255,255,255,0.12)"
									>
										<div
											class="h-full rounded-full transition-all duration-500"
											style="width:{pct(macro.val, mx)}%;background:{macro.color};"
										></div>
									</div>
								</div>
							{/each}
						</div>
						<div
							class="flex items-center justify-between pt-2"
							style="border-top:0.5px solid rgba(255,255,255,0.1)"
						>
							<span class="text-[10px] text-white/40 capitalize">{food.cat}</span>
							<span class="text-[13px] font-semibold text-white">{food.cal} kcal</span>
						</div>
					</div>
				</div>
			{/each}
		</div>
	{/if}

	<!-- ── EXERCISE CARDS ── -->
	{#if isExerciseMode}
		<div class="grid grid-cols-2 gap-3 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5">
			{#each exercises as ex (ex.name)}
				<div
					class="group relative cursor-pointer overflow-hidden rounded-2xl border
                 {ex.border} {ex.cardLight} {ex.cardDark}"
					style="aspect-ratio: 3/4;"
				>
					<!-- FRONT -->
					<div
						class="absolute inset-0 flex flex-col transition-opacity duration-300 group-hover:opacity-0"
					>
						<!-- emoji -->
						<div class="flex flex-1 items-center justify-center pt-3 text-5xl">{ex.emoji}</div>

						<div class="mx-3 border-t {ex.border} opacity-40"></div>

						<div class="flex flex-col gap-0.5 px-3 py-2.5">
							<p class="truncate text-xs leading-tight font-semibold {ex.textLight} {ex.textDark}">
								{ex.name}
							</p>
							<p class="truncate text-[10px] {ex.textLight} {ex.textDark} opacity-60">
								{ex.muscle}
							</p>
							<div class="mt-1.5 flex items-center justify-between">
								<!-- level badge -->
								<span class="text-[10px] font-medium {levelColor[ex.level]}">{ex.level}</span>
								<span class="text-[11px] font-bold {ex.textLight} {ex.textDark}"
									>{ex.sets}×{ex.reps}</span
								>
							</div>
						</div>
					</div>

					<!-- BACK -->
					<div
						class="absolute inset-0 flex flex-col justify-end rounded-2xl p-3 opacity-0 transition-opacity duration-300 group-hover:opacity-100"
						style="background:rgba(9,9,11,0.90);backdrop-filter:blur(6px);"
					>
						<p class="mb-0.5 truncate text-[14px] font-semibold text-white">{ex.name}</p>
						<p class="mb-3 truncate text-[10px] {levelColor[ex.level]}">{ex.level}</p>

						<!-- stats rows — same pattern as food macro rows -->
						<div class="mb-3 flex flex-col gap-2">
							<!-- Primary muscle -->
							<div class="flex items-center justify-between">
								<span class="text-[10px] text-white/60">Target</span>
								<span class="text-[10px] font-medium text-white">{ex.muscle}</span>
							</div>
							<div class="h-px w-full" style="background:rgba(255,255,255,0.08)"></div>

							<!-- Secondary -->
							<div class="flex items-center justify-between">
								<span class="text-[10px] text-white/60">Also</span>
								<span class="text-right text-[10px] font-medium text-white/80" style="max-width:60%"
									>{ex.secondary}</span
								>
							</div>
							<div class="h-px w-full" style="background:rgba(255,255,255,0.08)"></div>

							<!-- Sets × Reps -->
							<div class="flex items-center justify-between">
								<span class="text-[10px] text-white/60">Sets × Reps</span>
								<span class="text-[10px] font-medium text-white">{ex.sets} × {ex.reps}</span>
							</div>
							<div class="h-px w-full" style="background:rgba(255,255,255,0.08)"></div>

							<!-- Rest -->
							<div class="flex items-center justify-between">
								<span class="text-[10px] text-white/60">Rest</span>
								<span class="text-[10px] font-medium text-white">{ex.rest}</span>
							</div>
						</div>

						<!-- Footer -->
						<div
							class="flex items-center justify-between pt-2"
							style="border-top:0.5px solid rgba(255,255,255,0.1)"
						>
							<span class="text-[10px] text-white/40">exercise</span>
							<span class="text-[11px] font-semibold {levelColor[ex.level]}">{ex.level}</span>
						</div>
					</div>
				</div>
			{/each}
		</div>
	{/if}
</div>
