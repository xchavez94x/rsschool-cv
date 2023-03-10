## About me
- Ahmed Saadoon
- Highly motivated, always eager to learn new things, Although i sit at PC, i also  like to make a new friends. 
---
## Contacts 
#### Phone & Email
- +1-971-435-0118
- blackshock4@gmail.com
#### Social
- [Github](https://github.com/xchavez94x)
- [Linkedin](https://www.linkedin.com/in/ahmed-saadoon-1463aa1b9/)
- [Facebook](https://www.facebook.com/ahmed.marco.54/) 
- [Codewars](https://www.codewars.com/users/xchavez94x)
---
## Skills
- HTML, CSS, SCSS.
- Javascript.
- Mongodb, React js, Express js, Nodejs, & MySql.
- Basic Typescript skills.
- Some basic Angular.js skills.
- Some basic algorithms knowledge (search and sort algorithms) 
---
## Code example

```javascript
    import elements from "./elements.mjs";
    let cart = []

    const menuHandler = (e) => {
        const { mobileMenu, backdrop, cartElement } = elements;
        switch(e.target.id) {
            case('burger_menu'): {
                mobileMenu.classList.toggle('show_mobile_menu');
                backdrop.classList.add('showBackdrop');
                break;
            }
            case ('backdrop'): {
                mobileMenu.classList.remove('show_mobile_menu');
                backdrop.classList.remove('showBackdrop');
                cartElement.classList.remove('cart')
                break;
            }
            default: return 
        }
    }

    const fetchData = async () => {
        let fetchedData;
        try {
            let response = await fetch('https://fakestoreapi.com/products');
            fetchedData = await response.json();
        } catch(error) {
            console.log(error)
        }  
        console.log(fetchedData)
        return [ fetchedData ] 
    }

```
---
## Experience
- Customer support specialist 1.9 years.
- Web development 0.7 year.
---
## Education
- Kahrkiv ITStep academy.
- FreeCodeCamp.
- Udemy.
---
## English level
- Upper-intermediate (Skills from my job since i'm working in a US-based company. Plus, i've recently moved to the USA)
---
## Other languages
- Arabic(Native)
- Russian(advanced)