const recette = document.getElementById("recette");
function displayRecipes() {
  
    for (let i = 0; i < recettesDB.length; i++) {
      const recipe = recettesDB[i];
      let n=0;
    
      let cat= document.createElement("div");
      cat.classList.add("cat");

      let info = document.createElement("div");
      info.classList.add("infoc");
  
      let photo = document.createElement("div");
      photo.classList.add("pic");
      
      let img= document.createElement("img");
      img.setAttribute("src","/assets/recette/" + recipe.id + "/2.png");
  
      let nom = document.createElement("a");
      nom.setAttribute("href","detail.html?recette="+recipe.id);
      nom.innerText=recipe.name;

      let Catégorie = document.createElement("h3");
      Catégorie.innerText="Catégorie:"+recipe.category;
      
      let duration= document.createElement("h3");
      duration.innerText="Duration:"+recipe.duration;

      let pays = document.createElement("h3");
      pays.innerText="Pays:"+recipe.country;

      let note = document.createElement("h4");
      for (let j = 0; j < recettesDB[i].comments.length; j++) {
        n += recettesDB[i].comments[j].rating;
      }
      note.innerText ="Note: "+n / recettesDB[i].comments.length;

      photo.appendChild(img);

      info.appendChild(nom);
      info.appendChild(Catégorie);
      info.appendChild(duration);
      info.appendChild(pays);

      cat.appendChild(photo);
      cat.appendChild(info);

      recette.appendChild(cat);

    }
  }
 
const messageContainer = document.getElementById("messageContainer");
const searchInput = document.getElementById("sbr");
  function searchRecipe() {
    const searchTerm = searchInput.value.toLowerCase();
    let found = false;
    n=0;
    for (let i = 0; i < recettesDB.length; i++) {
      const recipe = recettesDB[i];
      const recipeName = recipe.name.toLowerCase();

      if (recipeName.includes(searchTerm)) {
        recette.innerHTML = "";
        const cat = document.createElement("div");
        cat.classList.add("cat");
  
        let info = document.createElement("div");
        info.classList.add("infoc");
        let photo = document.createElement("div");
        photo.classList.add("pic");
        
        let img= document.createElement("img");
        img.setAttribute("src","/assets/recette/" + recipe.id + "/2.png");
    
        let nom = document.createElement("a");
        nom.setAttribute("href","detail.html?recette="+recipe.id);
        nom.innerText=recipe.name;
  
        let Catégorie = document.createElement("h3");
        Catégorie.innerText="Catégorie:"+recipe.category;
        
        let duration= document.createElement("h3");
        duration.innerText="Duration:"+recipe.duration;
  
        let pays = document.createElement("h3");
        pays.innerText="Pays:"+recipe.country;
  
        let note = document.createElement("h4");
        for (let j = 0; j < recettesDB[i].comments.length; j++) {
          n += recettesDB[i].comments[j].rating;
        }
        note.innerText ="Note: "+n / recettesDB[i].comments.length;
  
        photo.appendChild(img);
  
        info.appendChild(nom);
        info.appendChild(Catégorie);
        info.appendChild(duration);
        info.appendChild(pays);
  
        cat.appendChild(photo);
        cat.appendChild(info);
  
        recette.appendChild(cat);
  
        found = true;
      }
    }
    if (!found) {
      messageContainer.innerHTML = "<h2>Nous somme désolé!la recette dont vous cherchez n'est pas disponible pour le moment<h2>";
      recette.style.display = "none";
      messageContainer.style.display = "block";
    } else {
      messageContainer.innerText = "";
    }
  }

  searchInput.addEventListener("keydown", (event) => {
    if (event.key === "Enter") {
      searchRecipe();
    }
  });