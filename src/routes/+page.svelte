<script lang="ts">
	import { resolve } from '$app/paths';
	import { Button } from '$lib/components/ui/button/index.js';
	import { Marquee } from '@selemondev/svelte-marquee';
	import '@selemondev/svelte-marquee/dist/style.css';
	import GithubIcon from '@lucide/svelte/icons/github';
	import * as Card from '$lib/components/ui/card/index.js';
	import MapPinIcon from '@lucide/svelte/icons/map-pin';
	import StarIcon from '@lucide/svelte/icons/star';
	import EyeIcon from '@lucide/svelte/icons/eye';
	import { Badge } from '$lib/components/ui/badge/index.js';
	import {
		DropdownMenu,
		DropdownMenuTrigger,
		DropdownMenuContent,
		DropdownMenuItem
	} from '$lib/components/ui/dropdown-menu/index.js';

	type University = {
		name: string;
		logo: string;
		locations: string[];
		priceRange: { min: number; max: number };
		reviews: { rating: number; count: number };
		views: number;
	};

	const universities: University[] = [
		{
			name: 'Universitas Terbuka',
			logo: '/logo/universities/ut.svg',
			locations: [
				'Jakarta, Indonesia',
				'Bogor, Indonesia',
				'Depok, Indonesia',
				'Bekasi, Indonesia'
			],
			priceRange: { min: 3200000, max: 4100000 },
			reviews: { rating: 4.6, count: 1320 },
			views: 12800
		},
		{
			name: 'Universitas Siber Asia',
			logo: '/logo/universities/ut.svg',
			locations: ['Yogyakarta, Indonesia', 'Semarang, Indonesia'],
			priceRange: { min: 3800000, max: 4600000 },
			reviews: { rating: 4.3, count: 860 },
			views: 7400
		},
		{
			name: 'Universitas Buka Raya',
			logo: '/logo/universities/ut.svg',
			locations: ['Bandung, Indonesia', 'Cimahi, Indonesia', 'Sumedang, Indonesia'],
			priceRange: { min: 3500000, max: 4200000 },
			reviews: { rating: 4.8, count: 2105 },
			views: 15400
		}
	];

	const formatIDR = (n: number): string => new Intl.NumberFormat('id-ID').format(n);
</script>

<header class="fixed inset-x-0 top-0 z-10">
	<div class="inner py-4">
		<div class="flex items-center justify-between">
			<a href={resolve('/')} class="text-lg font-bold text-gray-700">kulon.id</a>
			<div class="flex items-center gap-8">
				<div class="flex gap-6">
					<a class="text-gray-600 decoration-wavy hover:underline" href={resolve('/')}> Beranda </a>
					<a class="text-gray-600 decoration-wavy hover:underline" href={resolve('/')}>
						Universitas
					</a>
					<a class="text-gray-600 decoration-wavy hover:underline" href={resolve('/')}> Blog </a>
				</div>
				<div class="flex gap-1">
					<Button size="icon" variant="ghost">
						<GithubIcon />
					</Button>
					<Button>Gabung Komunitas</Button>
				</div>
			</div>
		</div>
	</div>
</header>

<main class="relative flex min-h-screen bg-linear-to-b from-[#4ED7F1] to-white">
	<div class="inner py-38">
		<div class="flex flex-col items-center">
			<span class="mb-2 text-center font-handwriting text-lg underline decoration-wavy">
				Semua Tentang Kuliah Online
			</span>
			<h1 class="max-w-4xl text-center text-6xl font-semibold">
				Kuliah Online itu Fleksibel. Temennya Juga Harus Ada.
			</h1>
			<p class="mt-6 max-w-lg text-center text-xl">
				Bandingkan jurusan, biaya, sistem belajar—plus ketemu orang-orang yang juga kuliah online.
			</p>
			<div class="mt-8 flex gap-2">
				<Button size="lg">Cari Kampus</Button>
				<Button size="lg" variant="outline">Cari Teman</Button>
			</div>
		</div>
		<Marquee
			innerClassName="mt-25"
			direction="left"
			fade={true}
			reverse={false}
			pauseOnHover={false}
		>
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
			<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
		</Marquee>
	</div>
	<img
		class="pointer-events-none absolute bottom-0 left-0"
		src="/decorations/cloud.png"
		alt="Cloud"
	/>
	<img
		class="pointer-events-none absolute right-0 bottom-0 -scale-x-100"
		src="/decorations/cloud.png"
		alt="Cloud"
	/>
</main>

<section>
	<div class="inner py-6">
		<h2 class="text-4xl font-semibold">Temukan Kampus Online yang Pas Buatmu</h2>
		<p class="mt-4 text-xl">Bandingkan universitas, jurusan, biaya, dan sistem belajar.</p>
		<div class="mt-8 grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each universities as u}
				<div class="relative overflow-hidden rounded-xl">
					<img
						src="https://www.ut.ac.id/wp-content/uploads/2025/03/Gerbang-Universitas-Terbuka-2025-768x524.jpg"
						alt=""
						class="aspect-video h-40 w-full object-cover"
					/>
					<Badge
						variant="secondary"
						class="absolute top-0 right-0 flex items-center rounded-none rounded-bl-md"
					>
						<EyeIcon class="size-3.5 text-muted-foreground" />
						<span class="text-muted-foreground">{formatIDR(u.views)}x dilihat</span>
					</Badge>
					<Card.Root class="relative -mt-4">
						<Card.Header>
							<img alt={u.name} src={u.logo} class="h-10 w-10 rounded-md" />
							<Card.Title class="text-2xl">{u.name}</Card.Title>
						</Card.Header>

						<Card.Content>
							<p class="text-muted-foreground">Rentang biaya per semester</p>
							<p class="mt-1 text-2xl font-semibold">
								Rp {formatIDR(u.priceRange.min)}–{formatIDR(u.priceRange.max)}
							</p>
						</Card.Content>
						<Card.Footer class="flex gap-2">
							<Button size="sm">Lihat detail</Button>
							<Button size="sm" variant="outline">Bandingkan</Button>
						</Card.Footer>
					</Card.Root>
				</div>
			{/each}
		</div>
	</div>
</section>
