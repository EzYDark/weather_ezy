<script lang="ts">
	import { Heading, P, Hr, ToolbarGroup, ButtonGroup, DarkMode } from 'flowbite-svelte';
	import { Button, Dropdown, DropdownItem, Chevron, Checkbox, Search } from 'flowbite-svelte';
	import WeatherCard from '$lib/components/WeatherCard.svelte';
	import DateTimeDisplay from '$lib/components/DateTimeDisplay.svelte';
	import LocationIcon from '$lib/components/LocationIcon.svelte';
	import DropdownIcon from '$lib/components/DropdownIcon.svelte';
	import WindIcon from '$lib/components/WindIcon.svelte';

	const cities = [
		'Berlin, Germany',
		'Frankfurt, Germany',
		'Dresden, Germany',
		'Plzeň, Czech Republic',
		'Ostrava, Czech Republic',
		'Prague, Czech Republic'
	];
</script>

<div class="flex bg-[url('$lib/images/sunny.png')] bg-cover bg-center bg-no-repeat">
	<div class="dark:bg-gray-700/20 p-10 flex flex-col h-screen backdrop-blur-sm">
		<div class="bg-yellow-500/0 w-full self-end flex flex-row">
			<div class="bg-blue-500/0">
				<DarkMode
					btnClass="text-white ring-2 ring-white dark:ring-gray-700 dark:text-gray-700 hover:bg-gray-700 dark:hover:bg-gray-100 rounded-lg text-sm p-2.5"
				/>
			</div>
			<div class="bg-green-500/0 flex flex-col w-full">
				<div class="flex flex-row bg-pink-500/0 self-end">
					<div>
						<DateTimeDisplay date="21 April 2023" class="dark:text-gray-900" />
					</div>
					<div>
						<Hr
							hrClass="w-8 h-1 rotate-90 translate-y-0.5 bg-white/60 dark:bg-gray-900/40 rounded border-0"
						/>
					</div>
					<div>
						<DateTimeDisplay date="15:00" class="dark:text-gray-900" />
					</div>
				</div>
			</div>
		</div>
		<div class="flex flex-row h-full">
			<div class="bg-red-500/0 w-full h-80 self-end flex flex-col">
				<div>
					<Heading
						tag="h2"
						class="text-right mb-7 dark:text-gray-900"
						customSize="text-7xl font-bold"
						color="text-white">Sunny</Heading
					>
					<Hr hrClass="w-full h-1 bg-white/60 dark:bg-gray-900/40 rounded border-0" />
				</div>
				<div class="flex flex-row overflow-x-auto scrollbar-hide h-full mt-7">
					<div class="grid grid-cols-10 gap-5 flex-shrink-0">
						{#each Array(10) as _}
							<WeatherCard
								class="dark:bg-gray-900/40 dark:hover:border-gray-200/20 dark:hover:bg-gray-700/40"
							/>
						{/each}
					</div>
				</div>
			</div>
		</div>
	</div>
	<div
		class="bg-gray-300/10 dark:bg-gray-900/40 p-10 h-screen flex-none w-96 backdrop-blur-lg border-x-2 border-white/40 dark:border-gray-900/40"
	>
		<div class="flex flex-col h-full">
			<div class="bg-pink-500/0 flex-none">
				<Button size="md" color="light" class="w-full justify-start focus:ring-0">
					<div class="bg-fuchsia-500/0 flex flex-row w-full">
						<div class="bg-yellow-500/0">
							<LocationIcon class="w-7 h-7 pr-2 text-gray-300" />
						</div>
						<div class="bg-green-500/0 w-full">
							<P size="base" weight="bold" color="text-gray-600" class="dark:text-gray-100"
								>Prague, Czech Republic</P
							>
						</div>
						<div class="bg-blue-500/0">
							<DropdownIcon class="w-7 h-7 pl-2 text-gray-300" />
						</div>
					</div>
				</Button>
				<Dropdown class="overflow-y-auto px-3 pb-3 text-sm h-44 scrollbar-hide">
					<div slot="header" class="p-3">
						<Search size="md" class="focus:" />
					</div>
					{#each cities as city}
						<li class="rounded p-1 hover:bg-gray-100">
							<DropdownItem>{city}</DropdownItem>
						</li>
					{/each}
				</Dropdown>
			</div>
			<div class="bg-blue-500/0 w-full h-52 flex flex-col flex-none">
				<div class="bg-pink-500/0 self-center py-10">
					<Heading tag="h2" color="text-white" customSize="text-7xl font-bold">11°C</Heading>
				</div>
				<div class="bg-gray-600/30 dark:bg-gray-900/40 flex flex-col w-full p-1 rounded-lg">
					<div class=" flex flex-row self-center">
						<WindIcon class="w-7 h-7 pr-2 text-gray-200" />
						<P size="base" weight="bold" color="text-gray-200">Northwest, 38.9 km/h</P>
					</div>
				</div>
				<Hr hrClass="w-full h-0.5 bg-white/60 dark:bg-gray-900/40 rounded border-0 mt-5" />
			</div>
			<div class="bg-green-500/0 w-full h-full flex flex-col">
				<div class="bg-pink-500/0 self-center my-6">
					<Heading tag="h3" color="text-white" customSize="text-2xl font-bold"
						>The Next Days Forecast</Heading
					>
				</div>
				<div class="bg-orange-500/0 w-full flex flex-col">
					<ButtonGroup class="self-center h-full">
						<Button color="light">5 days</Button>
						<Button color="light">14 days</Button>
						<Button color="light">30 days</Button>
					</ButtonGroup>
				</div>
				<div class="bg-purple-500/0 w-full h-full" />
			</div>
		</div>
	</div>
</div>
