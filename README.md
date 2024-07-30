# Assignment 1
- Hosted-Link - [https://simplyfi-frontend.vercel.app/]
## Explanation

- Resets margin and padding for all elements, sets box-sizing to border-box.
- Centers content both vertically and horizontally, sets the background color to dark gray, and uses a sans-serif font.
- Creates a square container for the logo and rotates it 45 degrees.
- Common styles for the bars in the logo, making them span the width of the logo and have a fixed height.
- Styles for individual bars (top, right, bottom, left), positioning them and setting their colors. The right and left bars are styled with additional borders to create a layered effect.
- Centers the text within the logo and rotates it back to align horizontally. The text2 class positions the subtext below the main text.

## Screenshot
![Screenshot from 2024-07-30 13-52-53](https://github.com/user-attachments/assets/3600b657-abc6-4def-ad71-c1964d943863)


# Assignment 2

- Q . Your son took a vacation through Europe without telling you. When the kid returned from the vacation you asked him where did he go. The kid told you: Dad I went to these cities: Amsterdam, Kiev, Zurich, Prague, Berlin, Barcelona.
  I used only train as transportation and these were the available tickets:
  Paris-Skopje, Zurich-Amsterdam, Prague-Zurich, Barcelona-Berlin, Kiev-Prague, Skopje-Paris, Amsterdam-Barcelona, Berlin-Kiev, Berlin-Amsterdam.
  You know that your kid started with Kiev.
  Write a data structure and algorithm that will give you the route which your son was traveling.
# Solution
```Solution
function findRoute(startCity, tickets) {
  let route = [startCity];
  let currentCity = startCity;
      while (route.length < 6) {
          for (let ticket of tickets) {
              let [from, to] = ticket.split('-');
              if (from === currentCity && !route.includes(to)) {
                  route.push(to);
                  currentCity = to;
                  break;
              }
          }
      }

      return route;
  }

const tickets = [
"Paris-Skopje", "Zurich-Amsterdam", "Prague-Zurich",
"Barcelona-Berlin", "Kiev-Prague", "Skopje-Paris",
"Amsterdam-Barcelona", "Berlin-Kiev", "Berlin-Amsterdam"
];
const startCity = "Kiev";
const travelRoute = findRoute(startCity, tickets);
console.log(travelRoute.join(" -> "));


```
# Explanation

- We define a findRoute function that takes the starting city and the list of tickets.
- We initialize the route array with the starting city and set the currentCity to the starting city.
- We use a while loop that continues until we've visited all 6 cities.

## Inside the loop, we iterate through the tickets:

- We split each ticket into 'from' and 'to' cities.
- If the 'from' city matches our current city and we haven't visited the 'to' city yet, we add the 'to' city to our route and make it our new current city.
- We then break out of the ticket loop to start looking for the next city.
- Once we've visited all cities, we return the route.

 When you run this code, it will output the route your son traveled:
 Kiev -> Prague -> Zurich -> Amsterdam -> Barcelona -> Berlin
