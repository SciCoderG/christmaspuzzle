
<script lang="ts">
	import { goto } from "$app/navigation";
    import { writable } from "svelte/store";

    $: number = ''
    $: isCorrect = number == "2433"
    $: feedback = '';


    function check(){
        if(isCorrect){
            feedback ='Richtig!';
            setTimeout(() => {
                goto('/correct'); // Ersetze '/neue-seite' mit dem Pfad der Zielseite
            }, 1000);
        } else {
            feedback = 'Falsch, versuche es nochmal!';
        }
    }


    function reset(){
        feedback=''
    }
</script>
<div class="hero min-h-screen bg-[url('/img/background_1.webp')]">
	<div class="hero-overlay bg-opacity-60" />
	<div class="hero-content text-center text-white	">
		<div class="max-w-md">
			<h1 class="mb-5 text-5xl font-bold">Ein wildes Weihnachtsrätsel erscheint!</h1>
			<p class="mb-5" />
			<div class="mb-5">
				<div class="gedicht">
					Tannengrün im Winterkleid, hält die Kälte fern, 
                    Leise deckt der Schnee die Welt, wir sehen ihn so gern, 
                    Durch die Nacht, das Glöckchen klingt, so froh und licht, 
                    Wie in jedem Jahr, kehrt das Fest zurück, 
                    Zählt die Worte leise, findet das verborgene Glück.
				</div>
			</div>

			<div class="p-4 text-center">
                <input type="text" 
                       id="numberInput" 
                       bind:value={number}
                       class="input input-bordered w-full max-w-xs text-center" 
                       maxlength="4" 
                       pattern="\d{4}" 
                       title="Vier Zahlen eingeben" 
                       on:input={reset} />
            
                <button class="btn btn-primary mt-2" on:click={check}>
                    Überprüfen
                </button>
                <p class="mt-2" class:richtig={isCorrect} class:falsch={!isCorrect}>
                    {feedback}
                </p>
            </div>
		</div>
	</div>
</div>

<style>
	.gedicht {
		white-space: pre-line;
	}

    .richtig {
        color: green;
        font-size: 24px;
        font-weight: bold;
    }
    .falsch {
        color: red;
    }
</style>
