<script lang="ts">
	import { resolve } from '$app/paths';
	import { Button } from '$lib/components/ui/button/index.js';
	import { Marquee } from '@selemondev/svelte-marquee';
	import '@selemondev/svelte-marquee/dist/style.css';
	import GithubIcon from '@lucide/svelte/icons/github';
	import * as Card from '$lib/components/ui/card/index.js';
	import EyeIcon from '@lucide/svelte/icons/eye';
	import { Badge } from '$lib/components/ui/badge/index.js';
	import * as Tooltip from '$lib/components/ui/tooltip/index.js';

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
			name: 'Terbuka',
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
			name: 'Siber Asia',
			logo: '/logo/universities/ut.svg',
			image: 'https://pmb.unsia.ac.id/uploads/asiacyberuniversity/imgpengumumanspmb/32.jpg',
			locations: ['Yogyakarta, Indonesia', 'Semarang, Indonesia'],
			priceRange: { min: 3800000, max: 4600000 },
			reviews: { rating: 4.3, count: 860 },
			views: 7400
		},
		{
			name: 'Insan Cita Indonesia',
			logo: '/logo/universities/ut.svg',
			image:
				'https://maukuliah.ap-south-1.linodeobjects.com/gallery/031070/1694509804-neIwacbhnd-thumbnail.jpg',
			locations: ['Jakarta, Indonesia', 'Tangerang, Indonesia'],
			priceRange: { min: 3500000, max: 4200000 },
			reviews: { rating: 4.5, count: 980 },
			views: 8900
		},
		{
			name: 'Bina Nusantara',
			logo: '/logo/universities/ut.svg',
			image:
				'https://cdn.antaranews.com/cache/1200x800/2023/06/02/WhatsApp-Image-2023-06-01-at-16.47.11.jpeg',
			locations: ['Jakarta, Indonesia', 'Bandung, Indonesia'],
			priceRange: { min: 4500000, max: 5500000 },
			reviews: { rating: 4.7, count: 1890 },
			views: 15600
		},
		{
			name: 'Ciputra',
			logo: '/logo/universities/ut.svg',
			image:
				'https://blog-static.mamikos.com/wp-content/uploads/2023/03/Universitas-Ciputra-1024x768.jpg',
			locations: ['Surabaya, Indonesia', 'Jakarta, Indonesia'],
			priceRange: { min: 4200000, max: 5200000 },
			reviews: { rating: 4.4, count: 1120 },
			views: 9800
		},
		{
			name: 'Indraprasta PGRI',
			logo: '/logo/universities/ut.svg',
			image: 'https://kelaskaryawan.net/wp-content/uploads/2016/06/Unindra.jpg',
			locations: ['Jakarta, Indonesia', 'Depok, Indonesia'],
			priceRange: { min: 3000000, max: 3800000 },
			reviews: { rating: 4.2, count: 750 },
			views: 6200
		},
		{
			name: 'Persada Indonesia Y.A.I',
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

<header class="fixed inset-x-0 top-0 z-10 border-b border-dashed border-border bg-background">
	<div class="inner border-x border-dashed border-border px-10 py-4">
		<div class="flex items-center justify-between">
			<a href={resolve('/')} class="text-lg font-bold text-gray-700">kampusdaring.com</a>
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

<main>
	<div class="inner border-x border-dashed border-border px-10 pt-38 pb-18">
		<div class="flex flex-col items-center">
			<span class="mb-2 text-center font-handwriting text-2xl">
				Portal Informasi Kuliah Online Terlengkap
			</span>
			<h1 class="max-w-4xl text-center text-6xl">
				Temukan Panduan Kuliah Online & Terhubung dengan Komunitas Belajar
			</h1>
			<p class="mt-6 max-w-lg text-center text-xl">
				Akses informasi komprehensif seputar perkuliahan online, program studi, dan tips akademik.
				Bergabung dengan komunitas untuk berdiskusi dan berbagi pengalaman.
			</p>
			<div class="mt-8 flex gap-2">
				<Button size="lg">Bergabung dengan Komunitas</Button>
				<Button size="lg" variant="outline">Jelajahi Direktori Universitas</Button>
			</div>
		</div>
		<Marquee innerClassName="mt-25" pauseOnHover>
			{#each Array(20) as _, i}
				<Tooltip.Provider delayDuration={0}>
					<Tooltip.Root>
						<Tooltip.Trigger>
							<img class="h-14" src="/logo/universities/ut.svg" alt="Universitas Terbuka" />
						</Tooltip.Trigger>
						<Tooltip.Content>Universitas Terbuka</Tooltip.Content>
					</Tooltip.Root>
				</Tooltip.Provider>
			{/each}
		</Marquee>
	</div>
</main>

<hr class="border-dashed border-border" />

<section>
	<div class="inner border-x border-dashed border-border p-10">
		<h2 class="text-5xl">Direktori Kampus Online</h2>
		<p class="mt-2 text-lg text-muted-foreground">
			Bandingkan universitas, jurusan, biaya, dan sistem belajar.
		</p>
		<div class="mt-12 grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
			{#each universities as u}
				<div
					class="relative flex flex-col overflow-hidden rounded-3xl border border-dashed border-border transition-transform duration-500 hover:-rotate-2"
				>
					<Badge
						variant="secondary"
						class="absolute top-0 right-0 flex items-center rounded-none rounded-bl-md bg-white"
					>
						<EyeIcon class="size-3.5 text-muted-foreground" />
						<span class="text-muted-foreground">{formatIDR(u.views)}x dilihat</span>
					</Badge>
					<div class="aspect-video h-40 w-full overflow-hidden rounded-2xl">
						<img class="size-full object-cover" src={u.image} alt={u.name} />
					</div>
					<Card.Root class="relative -mt-14 gap-4 border-none bg-transparent">
						<Card.Header class="gap-0">
							<div class="mb-2 flex size-16 items-center justify-center rounded-2xl bg-white">
								<img alt={u.name} src={u.logo} class="size-12" />
							</div>
							<p class="text-sm text-muted-foreground">Universitas</p>
							<Card.Title class="text-3xl">
								<h3>{u.name}</h3>
							</Card.Title>
						</Card.Header>

						<Card.Content>
							<p class="text-muted-foreground">Rentang biaya per semester</p>
							<p class="mt-1 text-xl">
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

<hr class="border-dashed border-border" />

<section>
	<div class="inner border-x border-dashed border-border p-10">
		<h2 class="text-5xl">Artikel & Insight</h2>
		<p class="mt-2 text-lg text-muted-foreground">
			Kumpulan tulisan seputar kampus online, pengalaman mahasiswa, tips belajar, dan perkembangan
			pendidikan digital.
		</p>
		<div class="flex flex-col">
			<hr class="my-10 border-dashed border-border" />

			<div class="flex gap-10">
				<div class="flex w-[200px] shrink-0 flex-col gap-1">
					<span class="text-lg">8 menit membaca</span>
					<span class="text-sm text-muted-foreground">02 Des 20</span>
					<div class="mt-4 flex items-center gap-2">
						<img
							class="aspect-square size-8 rounded-full"
							src="https://images.unsplash.com/photo-1761959939997-bde7210e7b1f?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=2342"
							alt="Siapa"
						/>
						<span class="text-sm text-muted-foreground">Abi Noval Fauzi</span>
					</div>
				</div>
				<div class="flex grow flex-col gap-2">
					<h3 class="text-3xl">Panduan Memilih Kampus Online yang Terakreditasi</h3>
					<p class="text-muted-foreground">
						Daftar kampus yang menyediakan pembelajaran 100% online. Lorem ipsum dolor sit amet
						consectetur.
					</p>
				</div>
				<div class="flex w-[200px] shrink-0 justify-end">
					<a href="/" class="text-muted-foreground underline hover:text-foreground"
						>Baca selengkapnya</a
					>
				</div>
			</div>

			<hr class="my-10 border-dashed border-border" />

			<div class="flex gap-10">
				<div class="flex w-[200px] shrink-0 flex-col gap-1">
					<span class="text-lg">8 menit membaca</span>
					<span class="text-sm text-muted-foreground">02 Des 20</span>
					<div class="mt-4 flex items-center gap-2">
						<img
							class="aspect-square size-8 rounded-full"
							src="https://images.unsplash.com/photo-1761959939997-bde7210e7b1f?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=2342"
							alt="Siapa"
						/>
						<span class="text-sm text-muted-foreground">Abi Noval Fauzi</span>
					</div>
				</div>
				<div class="flex grow flex-col gap-2">
					<h3 class="text-3xl">Panduan Memilih Kampus Online yang Terakreditasi</h3>
					<p class="text-muted-foreground">
						Daftar kampus yang menyediakan pembelajaran 100% online. Lorem ipsum dolor sit amet
						consectetur.
					</p>
				</div>
				<div class="flex w-[200px] shrink-0 justify-end">
					<a href="/" class="text-muted-foreground underline hover:text-foreground"
						>Baca selengkapnya</a
					>
				</div>
			</div>

			<hr class="my-10 border-dashed border-border" />

			<div class="flex gap-10">
				<div class="flex w-[200px] shrink-0 flex-col gap-1">
					<span class="text-lg">8 menit membaca</span>
					<span class="text-sm text-muted-foreground">02 Des 20</span>
					<div class="mt-4 flex items-center gap-2">
						<img
							class="aspect-square size-8 rounded-full"
							src="https://images.unsplash.com/photo-1761959939997-bde7210e7b1f?ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&q=80&w=2342"
							alt="Siapa"
						/>
						<span class="text-sm text-muted-foreground">Abi Noval Fauzi</span>
					</div>
				</div>
				<div class="flex grow flex-col gap-2">
					<h3 class="text-3xl">Panduan Memilih Kampus Online yang Terakreditasi</h3>
					<p class="text-muted-foreground">
						Daftar kampus yang menyediakan pembelajaran 100% online. Lorem ipsum dolor sit amet
						consectetur.
					</p>
				</div>
				<div class="flex w-[200px] shrink-0 justify-end">
					<a href="/" class="text-muted-foreground underline hover:text-foreground"
						>Baca selengkapnya</a
					>
				</div>
			</div>

			<hr class="my-10 border-dashed border-border" />
		</div>
	</div>
</section>
