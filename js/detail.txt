const recetteDetails = document.getElementById("recipeDetails"); 

function displayRecipeDetails() {
  const params = new URLSearchParams(window.location.search);
  const recipeId = params.get("recette");  

  for (let i = 0; i < recettesDB.length; i++) {
    const recipe = recettesDB[i];

    if (recipe.id == recipeId) {
      let n = 0;

      let descp = document.createElement("div");
      descp.classList.add("desp");

      let info = document.createElement("div");
      info.classList.add("info");

      let com = document.createElement("div");
      com.classList.add("com");

      let photo = document.createElement("div");
      photo.classList.add("pict");

      let img = document.createElement("img");
      img.setAttribute("src", "/assets/recette/" + recipe.id + "/2.png");

      let nom = document.createElement("h2");
      nom.innerText = recipe.name;
      nom.classList.add("nom");

      let Catégorie = document.createElement("h4");
      Catégorie.innerText="Catégorie:"+recipe.category;

      let pays = document.createElement("p");
      pays.innerText = "Pays: " + recipe.country;

      let duration = document.createElement("p");
      duration.innerText = "Durée: " + recipe.duration;

      let ingredients = document.createElement("div");
      ingredients.innerHTML = "<h3>Ingrédients:</h3><li>"+ recipe.ingredients.join("<li>");
      ingredients.classList.add("ing");

      let inst= document.createElement("div");
      inst.innerHTML = "<h3>Préparation:</h3><ol><li>" + recipe.instructions.join("<li>");
      inst.classList.add("inst");

      let comments = document.createElement("div");
      comments.innerHTML = "<h3>Commentaires:</h3>";
      comments.classList.add("comm");

      for (let j = 0; j < recipe.comments.length; j++) {
        let comment = recipe.comments[j];

        let user = document.createElement("p");
        user.innerHTML = "<li>Nom Utilisateur:" + comment.user;
        user.classList.add("user");

        let rating = document.createElement("p");
        rating.innerHTML = "Note:" + comment.rating;
        rating.classList.add("rating");

        let content = document.createElement("p");
        content.innerHTML = "Commentaire:" + comment.content;
        content.classList.add("con");

        comments.appendChild(user);
        comments.appendChild(rating);
        comments.appendChild(content);

        n += comment.rating;
      }

      let note = document.createElement("p");
      note.innerText = "Note: " + (n / recipe.comments.length).toFixed(1);

      photo.appendChild(img);
      photo.appendChild(nom);
      photo.appendChild(Catégorie);
      photo.appendChild(pays);
      photo.appendChild(duration);
      photo.appendChild(note);


      info.appendChild(ingredients);
      info.appendChild(inst);

      com.appendChild(comments);

      descp.appendChild(photo);
      descp.appendChild(info);
      descp.appendChild(com);

      recetteDetails.appendChild(descp);
    }
  }
}

displayRecipeDetails();
