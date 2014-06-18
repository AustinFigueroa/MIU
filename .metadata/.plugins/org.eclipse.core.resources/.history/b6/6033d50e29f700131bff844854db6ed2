Ti.UI.setBackgroundColor("#fff");

var pWidth = Ti.Platform.displayCaps.platformWidth;

var data = require("Json");

var mainWindow = Ti.UI.createWindow({
	title: "Champion List",
	backgroundColor: "#f5f5f5"
});

var navWindow = Ti.UI.iOS.createNavigationWindow({
	window: mainWindow
});

var champTables = Ti.UI.createTableView({
	top:0
	});

	if(Ti.Platform.name === "iPhone OS"){
		champTables.style = Ti.UI.iPhone.TableViewStyle.GROUPED;
	}

var champSection = Ti.UI.createTableViewSection({
	headerTitle: "",
	footerTitle: ""
});

var champSections = [champSection];
	champTables.setData(champSections);
	mainWindow.add(champTables);


var getDetail = function (){
	var detailWindow = Ti.UI.createWindow({
		title: this.title,
		font: {fontSize:10, fontFamily: "Arial", fontColor: "#000"},
	    backgroundColor: "#fff"
	});
	var detailImage = Ti.UI.createImageView({
		image: this.img,
		top: 5,
		left:5,
		imageAlign: "left"
	});
	var detailText = Ti.UI.createLabel({
		text: this.desc,
		font: {fontSize:14, fontFamily: "Arial", fontColor: "#000"},
		top: 25,
		left: 150,
		textAlign: "left"
	});
	var abilitiesButton = Ti.UI.createButton({
	title: "Abilities",
	backgroundColor: "#fff",
	textAlign: "center",
	font: {fontSize: 14, fontFamily: "Arial"},
	bottom: 125,
	width: pWidth,
	height:50
	});
	var openWindow = function(){
		var abilitiesWindow = Ti.UI.createWindow({
		title: "Abilities",
		font: {fontSize:10, fontFamily: "Arial", fontColor: "#000"},
	    backgroundColor: "#fff"
	});
	
	var abilitiesText = Ti.UI.createLabel({
		text: this.abilities,
		font: {fontSize:14, fontFamily: "Arial", fontColor: "#000"},
		top: 25,
		textAlign: "left"
	});
	
	navWindow.openWindow(abilitiesWindow);
	};
	
	abilitiesButton.addEventListener("click", openWindow);
	
	var loreButton = Ti.UI.createButton({
	title: "Lore",
	backgroundColor: "#fff",
	textAlign: "center",
	font: {fontSize: 14, fontFamily: "Arial"},
	bottom: 25,
	width: pWidth,
	height:50
});

var openWindow2 = function(){
    var loreWindow = Ti.UI.createWindow({
		title: "Lore",
		font: {fontSize:10, fontFamily: "Arial", fontColor: "#000"},
	    backgroundColor: "#fff"
	});
	var loreText = Ti.UI.createLabel({
		text: this.lores,
		font: {fontSize:14, fontFamily: "Arial", fontColor: "#000"},
		top: 25,
		textAlign: "left"
	});
	loreWindow.add(loreText);
	 navWindow.openWindow(loreWindow);
};
	loreButton.addEventListener("click", openWindow2);
	
	detailWindow.add(loreButton);
	detailWindow.add(abilitiesButton);
	detailWindow.add(detailImage);
	detailWindow.add(detailText);
	navWindow.openWindow(detailWindow);
   
};

for(n in data.champData){

	for(m in data.champData[n].championData){
		var theRow = Ti.UI.createTableViewRow({
		title: data.champData[n].championData[m].title,
		img: data.champData[n].championData[m].image,
		desc: data.champData[n].championData[m].description,
		abilities: data.champData[n].championData[m].ability,
		lores: data.champData[n].championData[m].lore,
	    hasChild: true
	});

	if(Ti.Platform.name === "iPhone OS"){
		theRow.hasChild = false;
		theRow.hasDetail = true;

	champSection.add(theRow);
	theRow.addEventListener("click", getDetail);
	};
	};	
};

navWindow.open();