<script context="module">
	import { browser, dev } from '$app/env';
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	});

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = true;
	// hydrate = true;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;
</script>

<script>
	function shuffle(array) {
		let currentIndex = array.length,
			randomIndex;

		// While there remain elements to shuffle.
		while (currentIndex != 0) {
			// Pick a remaining element.
			randomIndex = Math.floor(Math.random() * currentIndex);
			currentIndex--;

			// And swap it with the current element.
			[array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
		}

		return array;
	}

	const step1 = [
		{ title: '䷀', context: '凛凛皇者之象　自强不息之意', value: '乾为天' },
		{ title: '䷉', context: '如履虎尾之象　险中求胜之意', value: '天泽履' },
		{ title: '䷌', context: '二人同心之象　合作共事之意', value: '天火同人' },
		{ title: '䷘', context: '石中蕴玉之象　守旧安常之意', value: '天雷无妄' },
		{ title: '䷫', context: '风云际会之象　聚散随缘之意', value: '天风姤' },
		{ title: '䷅', context: '背道而驰之象　无端起讼之意', value: '天水讼' },
		{ title: '䷠', context: '守旧去恶之象　掘井无泉之意', value: '天山遁' },
		{ title: '䷋', context: '闭塞不通之象　上下不和之意', value: '天地否' }
	];

	const step2 = [
		{ title: '䷪', context: '蛟龙登天之象　亏中有益之意', value: '泽天夬' },
		{ title: '䷹', context: '天降雨泽之象　有誉有讥之意', value: '兑为泽' },
		{ title: '䷰', context: '豹变为虎之象　改旧纳新之意', value: '泽火革' },
		{ title: '䷐', context: '乘马逐鹿之象　随遇而安之意', value: '泽雷随' },
		{ title: '䷛', context: '枯木生花之象　反省过失之意', value: '泽风大过' },
		{ title: '䷮', context: '河中无水之象　守正待机之意', value: '泽水困' },
		{ title: '䷞', context: '山泽通气之象　往来无阻之意', value: '泽山咸' },
		{ title: '䷬', context: '鲤登龙门之象　精英荟萃之意', value: '泽地萃' }
	];

	const step3 = [
		{ title: '䷍', context: '日丽中天之象　好景不常之意', value: '火天大有' },
		{ title: '䷥', context: '二女同居之象　阴阳失调之意', value: '火泽睽' },
		{ title: '䷝', context: '丽日当天之象　光明远大之意', value: '离为火' },
		{ title: '䷔', context: '喉中有物之象　夫妻怨怒之意', value: '火雷噬嗑' },
		{ title: '䷱', context: '鼎器烹调之象　去故取新之意', value: '火风鼎' },
		{ title: '䷾', context: '阴阳失调之象　上下不通之意', value: '火水未济' },
		{ title: '䷷', context: '鸟焚其巢之象　乐极生悲之意', value: '火山旅' },
		{ title: '䷢', context: '满地锦绣之象　良臣遇君之意', value: '火地晋' }
	];

	const step4 = [
		{ title: '䷡', context: '猛处生角之象　声威大壮之意', value: '雷天大壮' },
		{ title: '䷵', context: '少女追男之象　错失端正之意', value: '雷泽归妹' },
		{ title: '䷶', context: '光明普照之象　弃暗投明之意', value: '雷火丰' },
		{ title: '䷲', context: '雷惊百里之象　惊恐不屈之意', value: '震为雷' },
		{ title: '䷟', context: '相对并行之象　努力不懈之意', value: '雷风恒' },
		{ title: '䷧', context: '草木舒展之象　遇困可解之意', value: '雷水解' },
		{ title: '䷽', context: '飞鸟遗音之象　阳奉阴违之意', value: '雷山小过' },
		{ title: '䷏', context: '雷奋大地之象　事见生机之意', value: '雷地豫' }
	];

	const step5 = [
		{ title: '䷈', context: '密云无雨之象　蓄养实力之意', value: '风天小畜' },
		{ title: '䷼', context: '鹤鸣子和之象　以诚待人之意', value: '风泽中孚' },
		{ title: '䷤', context: '入海求珠之象　开花结果之意', value: '风火家人' },
		{ title: '䷩', context: '风雷交错之象　损上益下之意', value: '风雷益' },
		{ title: '䷸', context: '飓风覆船之象　上行下效之意', value: '巽为风' },
		{ title: '䷺', context: '顺风扬帆之象　随波逐流之意', value: '风水涣' },
		{ title: '䷴', context: '草木渐茂之象　积小成多之意', value: '风山渐' },
		{ title: '䷓', context: '风扬尘埃之象　观察入微之意', value: '风地观' }
	];

	const step6 = [
		{ title: '䷄', context: '密云不雨之象　待机而动之意', value: '水天需' },
		{ title: '䷻', context: '蓄水成塘之象　勤检克己之意', value: '水泽节' },
		{ title: '䷾', context: '阴阳和谐之象　上下相通之意', value: '水火既济' },
		{ title: '䷂', context: '春木更新之象　艰难险阻之意', value: '水雷屯' },
		{ title: '䷯', context: '珠藏深渊之象　井井有条之意', value: '水风井' },
		{ title: '䷜', context: '重重险陷之象　向下内敛之意', value: '坎为水' },
		{ title: '䷦', context: '门前有陷之象　背明向暗之意', value: '水山蹇' },
		{ title: '䷇', context: '众星拱月之象　安逸进取之意', value: '水地比' }
	];

	const step7 = [
		{ title: '䷙', context: '浅水行舟之象　积小成大之意', value: '山天大畜' },
		{ title: '䷨', context: '山高水深之象　以德报怨之意', value: '山泽损' },
		{ title: '䷕', context: '争妍斗丽之象　粉饰庄扮之意', value: '山火贲' },
		{ title: '䷚', context: '匣中藏剑之象　审慎交往之意', value: '山雷颐' },
		{ title: '䷑', context: '物腐虫生之象　不进则退之意', value: '山风蛊' },
		{ title: '䷃', context: '童蒙启智之象　迷模摸索之意', value: '山水蒙' },
		{ title: '䷳', context: '重山关锁之象　步步为营之意', value: '艮为山' },
		{ title: '䷖', context: '群阴剥阳之象　去旧生新之意', value: '山地剥' }
	];

	const step8 = [
		{ title: '䷊', context: '事事通泰之象　上下和睦之意', value: '地天泰' },
		{ title: '䷒', context: '少女从母之象　循序渐进之意', value: '地泽临' },
		{ title: '䷣', context: '凤凰垂翼之象　弃明投暗之意', value: '地火明夷' },
		{ title: '䷗', context: '万物更新之象　重修破旧之意', value: '地雷復' },
		{ title: '䷭', context: '积小成大之象　拼搏得益之意', value: '地风升' },
		{ title: '䷆', context: '地势临渊之象　以寡服众之意', value: '地水师' },
		{ title: '䷎', context: '空谷藏玉之象　虚怀处世之意', value: '地山谦' },
		{ title: '䷁', context: '兼容万物之象　以柔制刚之意', value: '坤为地' }
	];

	let index = 0;
	$: current = step1;
	$: term = current[index]['title'];
	$: name = current[index]['value'];
	$: desc = current[index]['context'];

	let progress_step = 0;
	$: progress_step = (index + 1) / current.length;

	let result = '';
	let value = '';
	// let value2 = '';
	let rightCounter = 0;
	let wrongCounter = 0;

	let submitted = false;
	let isSuccessVisible = false;

	function handleSubmit(e) {
		isSuccessVisible = true;
		let input = value.trim().toLowerCase();
		checkAnswerHandler(input);
		progress.set(progress_step);
		value = '';
	}

	const reset = {
		soft: () => {
			current = shuffle(step1);
			value = '';
		},

		hard: () => {
			current = shuffle(current);
			index = 0;
			rightCounter = wrongCounter = 0;
			progress_step = 0;
			progress.set(progress_step);
			reset.soft();
			//console.log(step1);
		}
	};

	// to select all items into quiz
	function setALL() {
		const full_array = [
			...step1,
			...step2,
			...step3,
			...step4,
			...step5,
			...step6,
			...step7,
			...step8
		];
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	// to select all items into quiz
	function setONE() {
		const full_array = step1;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setTWO() {
		const full_array = step2;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setTHREE() {
		const full_array = step3;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setFOUR() {
		const full_array = step4;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setFIVE() {
		const full_array = step5;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setSIX() {
		const full_array = step6;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setSEVEN() {
		const full_array = step7;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	function setEIGHT() {
		const full_array = step8;
		shuffle(full_array);
		current = full_array;
		//console.log(current);

		return full_array;
	}

	// function modifyIndex() {
	// 	return (result = 'Answer is: ' + name);
	// 	setTimeout(function () {}, 2000);

	// 	// index += 1;
	// 	// wrongCounter += 1;

	// 	// console.log('skip.');

	// 	// Delay for 200 msecs so the input renders before we try to add focus
	// }

	const modifyIndex = {
		nextIndex: () => {
			index += 1;
			wrongCounter += 1;
		}
	};

	// event handler when answer is entered
	const handleKeyup = (event) => {
		if (event.key == 'Enter' && value !== '') {
			event.preventDefault();
			let input = value.trim().toLowerCase();
			checkAnswerHandler(input);
			progress.set(progress_step);
			value = '';
		}
		//console.log(value); print to console what I type
	};

	// check answer function
	function checkAnswerHandler(value) {
		const isCorrect = value === name;
		if (isCorrect) {
			rightCounter += 1;
			result = 'Correct';
			console.log('correct');
		} else {
			wrongCounter += 1;
			result = 'Incorrect ' + 'Answer is: ' + name;
			console.log('incorrect');
		}
		setTimeout(function () {
			index += 1;
			result = '';
		}, 2000); // to reset the result prompter and move to next question

		return result;
	}
</script>

<svelte:head>
	<title>易经六十四卦</title>
	<meta name="description" content="About this app" />
</svelte:head>

<section>
	<h1>
		<div class="welcome">易经六十四卦</div>
		<div class="flex flex-col text-center space-y-4 pb-7">
			<!-- <span class="text-lg md:text-2xl">What is the meaning of...</span> -->
			<span class="break-all text-4xl md:text-8xl mx-8">{term}</span>
			<span class="break-all text-1xl md:text-2xl mx-8">{desc}</span>
			<span class="inline-flex justify-center items-center">{result}</span>
			<progress value={$progress} />
		</div>
	</h1>
	<div class="flex-col text-center space-y-4 pb-3 space-x-4 text-gray-700 tabular-nums">
		Select Mode:
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setALL}>全 64卦</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setONE}>乾</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setTWO}>兌</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setTHREE}>離</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setFOUR}>震</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setFIVE}>巽</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setSIX}>坎</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setSEVEN}>艮</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={setEIGHT}>坤</button
		>
	</div>
	<!-- <div class="flex-col text-center space-y-4 pb-5 space-x-4 text-gray-700 tabular-nums">
		Select Mode:
		{#each todos as todo}
			<div>
				<button
					class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
					on:click={() => checker((value2 = todo.text))}>{todo.text}</button
				>
			</div>
		{/each}
	</div> -->

	<div class="flex-col text-center space-y-4 pb-10 space-x-4 text-gray-700 tabular-nums">
		Your Score:
		<span class="inline-flex justify-center items-center bg-green-200 w-10 h-8 rounded-md">
			{rightCounter}
		</span>
		<span class="inline-flex justify-center items-center bg-red-200 w-10 h-8 rounded-md">
			{wrongCounter}
		</span>
		<span class="inline-flex justify-center items-center bg-blue-200 w-20 h-8 rounded-md">
			{index + 1}/{current.length}
		</span>

		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={modifyIndex.nextIndex}>Skip</button
		>
		<button
			class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
			on:click={reset.hard}>Reset</button
		>
	</div>

	<div class="flex flex-col text-center space-y-4 pb-7">
		<!-- <input
			type="text"
			class="max-w-lg w-full p-4 my-2 border border-gray-300 rounded-md"
			placeholder="卦名"
			bind:value
			on:keyup|preventDefault={handleKeyup}
		/> -->
		<form class:submitted on:submit|preventDefault={handleSubmit}>
			<input
				type="text"
				class="max-w-lg w-full p-4 my-2 border border-gray-300 rounded-md"
				placeholder="卦名"
				bind:value
				on:keyup|preventDefault={handleKeyup}
			/>
			<button
				class="ml-auto px-4 py-1 border border-gray-200 bg-gray-200 text-gray-700 rounded-md hover:bg-red-500 hover:text-white"
				on:click={() => (submitted = true)}>submit</button
			>
		</form>
	</div>
</section>

<style>
	progress {
		display: block;
		width: 100%;
		/* background-color: blue; */
	}
</style>
