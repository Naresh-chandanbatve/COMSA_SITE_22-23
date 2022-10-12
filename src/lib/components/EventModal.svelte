<div class="modal-container">
	<img class="image" src="http://placeimg.com/400/400/tech" alt="Event Description" />
	<div class="text-container">
		<h1 class="title">Heading</h1>
		<div class="date">Date: Yes</div>
		<div class="description">
			<p>
				Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tenetur iure harum quam sequi
				dolor sapiente corrupti, quos praesentium exercitationem quibusdam distinctio ducimus fugit
				expedita? Nostrum quia corrupti facere neque rerum!
			</p>
			<p>
				Lorem ipsum dolor sit amet consectetur adipisicing elit. Voluptatem sint provident id
				doloribus minima non odio maxime beatae dignissimos quos voluptatibus doloremque perferendis
				qui asperiores, autem necessitatibus dolore officiis nobis.
			</p>
		</div>
		<div class="button-container">
			<button class="btn btn-primary" id="btn-1">Button1</button>
			<button class="btn btn-secondary" id="btn-2">Button2</button>
		</div>
	</div>
</div>

<style>
.modal-container {
    background-color: blueviolet;
    padding: 2rem;

    display: flex;
    flex-direction: column;
    
    @apply w-full h-full;
}

.image {
    max-width: 70vw;
    max-height: auto;
    border-radius: 1rem 1rem 0 0;
}


.text-container {
    max-width: 70vw;
    background-color: red;
    padding: .5rem 1rem;
    border-radius: 0 0 1rem 1rem;
}

@media only screen and (max-width: 640px) {
    .image {
        max-width: 80vw;
    }
    .text-container {
        max-width: 80vw;
    }
}


@media only screen and (max-width: 480px) {
    .image {
        max-width: 90vw;
    }
    .text-container {
        max-width: 90vw;
    }
}


.title {
    line-height: 3.75rem;
    font-size: 3.5rem;
    padding: 0.5rem;
}

.date {
    background-color: yellow;
    margin: 0 0 1rem 0;
    line-height: 1.75rem;
    font-size: 1.5rem;
}

.description {
    background-color: aqua;
    padding: 0.5rem;
    margin-bottom: 1rem;
    font-size: 1.05rem;
}

.button-container {
    background-color: darkgreen;
    padding: 0.5rem;
    display: inline-flex;
    width: 100%;
    justify-content: space-evenly;
    /* align-items: ; */
}

.btn {
    font-size: large;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    background-color: blue;
}

.btn-primary {
    background-color: #00B7A8;
}

.btn-secondary {
    background-color: #096386;
}

@media only screen and (min-width: 824px) {
    .modal-container {
        flex-direction: row;
        max-width: 90vw;
    }

    .image {
        max-width: 40vw;
        max-height: auto;
        border-radius: 1rem 0 0 1rem;
    }

    .text-container {
        border-radius: 0 1rem 1rem 0;
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
    }
}
</style>