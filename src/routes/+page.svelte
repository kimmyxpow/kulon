<script lang="ts">
	import { resolve } from '$app/paths';
	import { Button } from '$lib/components/ui/button/index.js';
	import { Marquee } from '@selemondev/svelte-marquee';
	import '@selemondev/svelte-marquee/dist/style.css';
	import GithubIcon from '@lucide/svelte/icons/github';
	import * as Card from '$lib/components/ui/card/index.js';
	import EyeIcon from '@lucide/svelte/icons/eye';
	import { Badge } from '$lib/components/ui/badge/index.js';

	type University = {
		name: string;
		logo: string;
		image: string;
		locations: string[];
		priceRange: { min: number; max: number };
		reviews: { rating: number; count: number };
		views: number;
	};

	const universities: University[] = [
		{
			name: 'Universitas Terbuka',
			logo: '/logo/universities/ut.svg',
			image:
				'https://www.ut.ac.id/wp-content/uploads/2025/03/Gerbang-Universitas-Terbuka-2025-768x524.jpg',
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
			image: 'https://pmb.unsia.ac.id/uploads/asiacyberuniversity/imgpengumumanspmb/32.jpg',
			locations: ['Yogyakarta, Indonesia', 'Semarang, Indonesia'],
			priceRange: { min: 3800000, max: 4600000 },
			reviews: { rating: 4.3, count: 860 },
			views: 7400
		},
		{
			name: 'Universitas Insan Cita Indonesia',
			logo: '/logo/universities/ut.svg',
			image:
				'https://maukuliah.ap-south-1.linodeobjects.com/gallery/031070/1694509804-neIwacbhnd-thumbnail.jpg',
			locations: ['Jakarta, Indonesia', 'Tangerang, Indonesia'],
			priceRange: { min: 3500000, max: 4200000 },
			reviews: { rating: 4.5, count: 980 },
			views: 8900
		},
		{
			name: 'Universitas Bina Nusantara',
			logo: '/logo/universities/ut.svg',
			image:
				'https://cdn.antaranews.com/cache/1200x800/2023/06/02/WhatsApp-Image-2023-06-01-at-16.47.11.jpeg',
			locations: ['Jakarta, Indonesia', 'Bandung, Indonesia'],
			priceRange: { min: 4500000, max: 5500000 },
			reviews: { rating: 4.7, count: 1890 },
			views: 15600
		},
		{
			name: 'Universitas Ciputra',
			logo: '/logo/universities/ut.svg',
			image:
				'https://blog-static.mamikos.com/wp-content/uploads/2023/03/Universitas-Ciputra-1024x768.jpg',
			locations: ['Surabaya, Indonesia', 'Jakarta, Indonesia'],
			priceRange: { min: 4200000, max: 5200000 },
			reviews: { rating: 4.4, count: 1120 },
			views: 9800
		},
		{
			name: 'Universitas Indraprasta PGRI',
			logo: '/logo/universities/ut.svg',
			image: 'https://kelaskaryawan.net/wp-content/uploads/2016/06/Unindra.jpg',
			locations: ['Jakarta, Indonesia', 'Depok, Indonesia'],
			priceRange: { min: 3000000, max: 3800000 },
			reviews: { rating: 4.2, count: 750 },
			views: 6200
		},
		{
			name: 'Universitas Persada Indonesia Y.A.I',
			logo: '/logo/universities/ut.svg',
			image:
				'https://www.streetdirectory.com/stock_images/indonesia/simg_show/ind_11833666970366/1/universitas_persada_indonesia_yai/',
			locations: ['Jakarta, Indonesia'],
			priceRange: { min: 3600000, max: 4400000 },
			reviews: { rating: 4.1, count: 680 },
			views: 5900
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

<hr class="border-dashed border-border" />

<section>
	<div class="inner border-x border-dashed border-border p-10">
		<h2 class="text-3xl font-semibold">Temukan Kampus Online yang Pas Buatmu</h2>
		<p class="mt-2 text-muted-foreground">
			Bandingkan universitas, jurusan, biaya, dan sistem belajar.
		</p>
		<div class="mt-12 grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each universities as u}
				<div class="relative overflow-hidden rounded-xl">
					<img src={u.image} alt={u.name} class="aspect-video h-40 w-full object-cover" />
					<Badge
						variant="secondary"
						class="absolute top-0 right-0 flex items-center rounded-none rounded-bl-md"
					>
						<EyeIcon class="size-3.5 text-muted-foreground" />
						<span class="text-muted-foreground">{formatIDR(u.views)}x dilihat</span>
					</Badge>
					<Card.Root class="relative -mt-4">
						<Card.Header>
							<img alt={u.name} src={u.logo} class="size-10" />
							<Card.Title class="text-2xl">{u.name}</Card.Title>
						</Card.Header>

						<Card.Content>
							<p class="text-muted-foreground">Rentang biaya per semester</p>
							<p class="mt-1 text-xl font-semibold">
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
