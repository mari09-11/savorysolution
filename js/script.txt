
function gotoplus() {window.location.href = "catalogue.html";}

function getRandomRecipes() {
  let recipe = [...recettesDB];
  const selectedRecipes = [];
  for (let i = 0; i < 4; i++) {
    const randomIndex = Math.floor(Math.random() * recipe.length);
    const selectedRecipe = recipe.splice(randomIndex, 1)[0];
    selectedRecipes.push(selectedRecipe);
  }
  return selectedRecipes;
}

function displayRandomRecipes() {
  const recipes = getRandomRecipes();
 
  const recipe1Div = document.getElementById('recipe1');
  recipe1Div.innerHTML = `<h3>${recipes[0].name}</h3>`;
  const img1Div = document.getElementById('img1');
  imagp="/assets/recette/"+recipes[0].id+"/2.png";
  imgElement = document.createElement("img");
  imgElement.src = imagp;
  img1Div.innerHTML = ""; 
  img1Div.appendChild(imgElement);
  
  const recipe2Div = document.getElementById('recipe2');
  recipe2Div.innerHTML = `<h3>${recipes[1].name}</h3>`;
  const img2Div = document.getElementById('img2');
  imagp="/assets/recette/"+recipes[1].id+"/2.png";
  imgElement = document.createElement("img");
  imgElement.src = imagp;
  img2Div.innerHTML = ""; 
  img2Div.appendChild(imgElement);
  
  
  const recipe3Div = document.getElementById('recipe3');
  recipe3Div.innerHTML = `<h3>${recipes[2].name}</h3>`;
  const img3Div = document.getElementById('img3');
  imagp="/assets/recette/"+recipes[2].id+"/2.png";
  imgElement = document.createElement("img");
  imgElement.src = imagp;
  img3Div.innerHTML = ""; 
  img3Div.appendChild(imgElement);
  
  
  const recipe4Div = document.getElementById('recipe4');
  recipe4Div.innerHTML = `<h3>${recipes[3].name}</h3>`;
  const img4Div = document.getElementById('img4');
  imagp="/assets/recette/"+recipes[3].id+"/2.png";
  imgElement = document.createElement("img");
  imgElement.src = imagp;
  img4Div.innerHTML = ""; 
  img4Div.appendChild(imgElement);
  
}

displayRandomRecipes();

