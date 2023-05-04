# Actor - Instructables Scraper

## Instructables scraper

Since Instructables doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Instructables data scraper supports the following features:

-   Search any keyword - You can search anything, filter anything and get everything!

-   Scrape categories, lists and more - All the listing pages that contains projects are already supported.

-   Scrape projects of a user - Looking forward to all the projects of a specific user? No problem. Just type the URL and get them right away.

-   Scrape user detail - If you are looking for some data about a specific user, you can directly provide the URL of the user and retrieve all the information.

-   Scrape project detail - Retrieve title, description, number of likes, number of comments, the steps and many other attributes in a structured format.

-   Scrape comments of a project - Directly get any of the comments that has been commited into a project. No limits and extremely fast!

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/instructables-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Instructables that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Instructables.

- `startUrls`: (Optional) (Array) List of Instructables URLs. You should only provide list, search, category, user, user projects or project detail URLs.

- `includeComments`: (Optional) (Boolean) This will add all the comments that Instructables provides into the project objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of comments.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.15-0.35 compute units.

### Instructables Scraper Input example

```json
{
  "startUrls":[
    "https://www.instructables.com/member/zaphodd42/",
    "https://www.instructables.com/Make-PVC-Look-Like-Wood/",
    "https://www.instructables.com/search/?q=project&projects=all",
    "https://www.instructables.com/living/",
    "https://www.instructables.com/member/zaphodd42/instructables/"
  ],
  "includeComments":false,
  "maxItems":10,
  "endPage":2,
  "proxy":{
    "useApifyProxy": true
  }
}

```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Instructables Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Instructables actor.

## Scraped Instructables Properties

The structure of each item in Instructables looks like this:

### Project Detail

```json
{
	"type": "project",
	"url": "https://www.instructables.com/Print-a-Helicone-Tinkercad3D-Printing",
	"title": "Print a Helicone! (Tinkercad/3D Printing)",
	"isFeatured": true,
	"numberOfViews": 13933,
	"numberOfLikes": 34,
	"numberOfComments": 6,
	"categories": [
		"Workshop",
		"3D Printing"
	],
	"steps": [
		{
			"title": "Introduction: Print a Helicone! (Tinkercad/3D Printing)",
			"media": [
				{
					"src": "https://content.instructables.com/FMX/73P5/KTMY2GVE/FMX73P5KTMY2GVE.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Print a Helicone! (Tinkercad/3D Printing)"
				},
				{
					"src": "https://content.instructables.com/FS6/S1LE/KTMY2H5W/FS6S1LEKTMY2H5W.jpg?auto=webp&fit=bounds&frame=1&height=1024&width=1024auto=webp&frame=1&height=300",
					"alt": "Print a Helicone! (Tinkercad/3D Printing)"
				},
				{
					"src": "https://content.instructables.com/FX7/OAVJ/KTMY2H5X/FX7OAVJKTMY2H5X.jpg?auto=webp&fit=bounds&frame=1&height=1024&width=1024auto=webp&frame=1&height=300",
					"alt": "Print a Helicone! (Tinkercad/3D Printing)"
				}
			],
			"body": "So a little while back I discovered the incredible 3D artist John Edmark - seriously, check his stuff out, it's incredible!! He'd invented something called a helicone - a tree like structure that resembles a helix but after being spun it transforms into a pinecone and then back again when spun the other way! I was pretty mesmerised by it and I reallywanted one!! Now, this is not an exact copy - it's certainly inspired by the original but if you want one exactly like John Edmark's, you can buy them on his website or through Amazon - I'm trying to challenge myself in terms of designing new models and trying to get into creating my own rather than buying wherever possible so I thought I'd see if I couldn't reverse engineer something similar from the photos and videos!If you just want the stls I made, feel free to jump ahead to the 'Print' step where I've included my stls but if you're interested in making your own or following my design process then I'll be running through that first :)You can also just download my STLs here on Thangs for free"
		},
		{
			"title": "Step 1: Making the Branches - Creating the Overall Shape",
			"media": [
				{
					"src": "https://content.instructables.com/FEP/DPQR/KTMY2O18/FEPDPQRKTMY2O18.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Overall Shape"
				},
				{
					"src": "https://content.instructables.com/FTW/XBBQ/KTMY2O1G/FTWXBBQKTMY2O1G.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Overall Shape"
				},
				{
					"src": "https://content.instructables.com/FG5/0JVD/KTMY2O16/FG50JVDKTMY2O16.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Overall Shape"
				}
			],
			"body": "Let's start with the most involved piece - the branches!These are made up of some very simple shapes really but I'm going to spread the process out over a few steps so I can include lots of pictures and screenshots - I find that pictures are significantly easier to follow than words with things like this!Let's start with the overall shape:Take a cylinder shape (20x20x2mm) and place it on the workplane Take a box shape (60x8x2mm) and align it with the cylinder so it runs across the centreTake a shape of your choice - I used hearts (25x27x2mm) and place one at each end of the box shapeYou've now created the basis for every branch you'll print!"
		},
		{
			"title": "Step 2: Making the Branches - Creating the Holes! 1/2",
			"media": [
				{
					"src": "https://content.instructables.com/FYS/DKP0/KTMY2O20/FYSDKP0KTMY2O20.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Holes! 1/2"
				},
				{
					"src": "https://content.instructables.com/FIP/KAKU/KTMY2O1W/FIPKAKUKTMY2O1W.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Holes! 1/2"
				},
				{
					"src": "https://content.instructables.com/F4E/SGV0/KTMY2O1X/F4ESGV0KTMY2O1X.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Holes! 1/2"
				},
				{
					"src": "https://content.instructables.com/FFW/1P2O/KTMY2O1Y/FFW1P2OKTMY2O1Y.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Holes! 1/2"
				},
				{
					"src": "https://content.instructables.com/FU5/1ZUU/KTMY2O1Z/FU51ZUUKTMY2O1Z.png?auto=webp&fit=bounds&frame=1auto=webp&frame=1&height=300",
					"alt": "Making the Branches - Creating the Holes! 1/2"
				}
			],
			"body": "Next we'll create the holes in the branch pieces that allow it to slot onto the rod and which enable the transformation when it spins!I've again split this into 2 parts just so it's easier to follow!Take a cylinder (20x20x2mm) Place a cylindrical hole in the centre of your cylinder (10x10mm) Place a box shaped hole (20x3mm) aligned with the centre of the original cylinderMake a duplicate of the box hole and rotate it by 69 degrees before grouping the cylinder with all 3 holesCut away the larger sections that are left - I just used several box shaped holesYou should be left with 2 small arc shapes at this point"
		}
	],
	"author": {
		"name": "ArKay894More by the author:bobb275ArKay894Amit_JainnasirakawaiicreaterJosiah Miller",
		"image": "https://content.instructables.com/FQU/TLQ2/KLP60SY7/FQUTLQ2KLP60SY7.jpg?auto=webp&crop=1%3A1&frame=1&width=130",
		"url": "https://www.instructables.com/member/ArKay894/"
	}
}
```

### User Detail

```json
{
	"type": "user",
	"url": "https://www.instructables.com/member/zaphodd42/",
	"name": "zaphodd42",
	"image": "https://content.instructables.com/FPW/BD89/IBYX09JZ/FPWBD89IBYX09JZ.jpg?auto=webp&crop=1%3A1&frame=1&width=150",
	"bio": "I live in suburban Pennsylvania with my wife and puppy. I pass the time building robots, photographing microbes and directing live TV.  I enjoy learning any new skill that helps me Make!  I enjoy even more passing on what I learned so others can Make as well.",
	"joinedAt": "Joined February 11th, 2009",
	"numberOfProjects": 77,
	"numberOfViews": 3908220,
	"numberOfComments": 387,
	"numberOfFollowers": 455,
	"location": "Pottstown, PA",
	"achievements": [
		{
			"name": "100+ Comments",
			"description": "Earned a bronze medal"
		},
		{
			"name": "1M+ Views",
			"description": "Earned a silver medal"
		},
		{
			"name": "1+ Featured Instructable",
			"description": "Earned a bronze medal"
		},
		{
			"name": "Contest Winner",
			"description": "First Prize in the  Before and After Contest"
		},
		{
			"name": "Contest Winner",
			"description": "Runner Up in the  PVC Challenge"
		}
	]
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that is available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
