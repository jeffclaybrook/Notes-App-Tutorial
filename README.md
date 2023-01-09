# Notes App Tutorial
Build a simple notes app with HTML, CSS, and JavaScript

## TLDR;
- Semantic HTML
- CSS with toggling layout
- JavaScript with arrow functions
- Local storage

### Demo link:
https://jeffclaybrook.github.io/Notes-App-Tutorial/

### Overview
In this tutorial, you'll create a note taking application using HTML, CSS, and JavaScript.

- Create notes
- Edit notes
- Delete notes
- Save notes to local storage
- Search notes
- Toggle between grid-view / list-view
- Expanding / collapsing bottom sheet

### Roboto Flex Stylesheet Link:
https://fonts.googleapis.com/css2?family=Roboto+Flex:opsz,wght@8..144,300;8..144,400;8..144,500;8..144,600&display=swap

### CSS - SVG Data URIs:
.add-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 36 36' width='36' height='36'%3E%3Cpath fill='%2334A853' d='M16 16v14h4V20z'%3E%3C/path%3E%3Cpath fill='%234285F4' d='M30 16H20l-4 4h14z'%3E%3C/path%3E%3Cpath fill='%23FBBC05' d='M6 16v4h10l4-4z'%3E%3C/path%3E%3Cpath fill='%23EA4335' d='M20 16V6h-4v14z'%3E%3C/path%3E%3Cpath fill='none' d='M0 0h36v36H0z'%3E%3C/path%3E%3C/svg%3E") no-repeat center center / cover;
    width: 2rem;
    height: 2rem;
}

.back-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='m11.1 19.1-6.45-6.475q-.15-.125-.212-.288-.063-.162-.063-.337 0-.175.063-.338.062-.162.212-.287L11.1 4.9q.225-.2.525-.213.3-.012.525.213.225.225.237.525.013.3-.212.55l-5.3 5.275H18.5q.3 0 .525.212.225.213.225.538 0 .325-.225.537-.225.213-.525.213H6.875l5.3 5.3q.2.2.212.512.013.313-.212.538-.225.225-.537.225-.313 0-.538-.225Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.delete-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='M7.3 20.5q-.75 0-1.275-.525Q5.5 19.45 5.5 18.7V6h-.25q-.325 0-.537-.213Q4.5 5.575 4.5 5.25q0-.325.213-.537.212-.213.537-.213H9q0-.375.262-.625.263-.25.638-.25h4.2q.375 0 .638.25.262.25.262.625h3.75q.325 0 .538.213.212.212.212.537 0 .325-.212.537Q19.075 6 18.75 6h-.25v12.7q0 .75-.525 1.275-.525.525-1.275.525ZM7 6v12.7q0 .125.088.213.087.087.212.087h9.4q.125 0 .213-.087.087-.088.087-.213V6Zm2.4 10.25q0 .325.213.538.212.212.537.212.325 0 .538-.212.212-.213.212-.538v-7.5q0-.325-.212-.538Q10.475 8 10.15 8q-.325 0-.537.212-.213.213-.213.538Zm3.7 0q0 .325.212.538.213.212.538.212.325 0 .538-.212.212-.213.212-.538v-7.5q0-.325-.212-.538Q14.175 8 13.85 8q-.325 0-.538.212-.212.213-.212.538ZM7 6v12.7q0 .125.088.213.087.087.212.087H7V6Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.grid-view-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='M5 11q-.625 0-1.062-.438Q3.5 10.125 3.5 9.5V5q0-.625.438-1.062Q4.375 3.5 5 3.5h4.5q.625 0 1.062.438Q11 4.375 11 5v4.5q0 .625-.438 1.062Q10.125 11 9.5 11Zm0 9.5q-.625 0-1.062-.438Q3.5 19.625 3.5 19v-4.5q0-.625.438-1.062Q4.375 13 5 13h4.5q.625 0 1.062.438.438.437.438 1.062V19q0 .625-.438 1.062-.437.438-1.062.438Zm9.5-9.5q-.625 0-1.062-.438Q13 10.125 13 9.5V5q0-.625.438-1.062.437-.438 1.062-.438H19q.625 0 1.062.438.438.437.438 1.062v4.5q0 .625-.438 1.062Q19.625 11 19 11Zm0 9.5q-.625 0-1.062-.438Q13 19.625 13 19v-4.5q0-.625.438-1.062Q13.875 13 14.5 13H19q.625 0 1.062.438.438.437.438 1.062V19q0 .625-.438 1.062-.437.438-1.062.438ZM5 9.5h4.5V5H5Zm9.5 0H19V5h-4.5Zm0 9.5H19v-4.5h-4.5ZM5 19h4.5v-4.5H5Zm9.5-9.5Zm0 5Zm-5 0Zm0-5Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.list-view-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='M5.3 10.8q-.75 0-1.275-.525Q3.5 9.75 3.5 9V5.625q0-.775.525-1.3T5.3 3.8h13.4q.75 0 1.275.525.525.525.525 1.3V9q0 .75-.525 1.275-.525.525-1.275.525Zm0-1.5h13.4q.1 0 .2-.088.1-.087.1-.212V5.625q0-.125-.1-.225t-.2-.1H5.3q-.1 0-.2.1t-.1.225V9q0 .125.1.212.1.088.2.088Zm0 10.9q-.75 0-1.275-.525-.525-.525-.525-1.3V15q0-.75.525-1.275Q4.55 13.2 5.3 13.2h13.4q.75 0 1.275.525.525.525.525 1.275v3.375q0 .775-.525 1.3T18.7 20.2Zm0-1.5h13.4q.1 0 .2-.1t.1-.225V15q0-.125-.1-.213-.1-.087-.2-.087H5.3q-.1 0-.2.087-.1.088-.1.213v3.375q0 .125.1.225t.2.1ZM5 5.3v4-4Zm0 9.4v4-4Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.menu-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='M4 17.625q-.325 0-.537-.212-.213-.213-.213-.538 0-.3.213-.525.212-.225.537-.225h16q.325 0 .538.225.212.225.212.525 0 .325-.212.538-.213.212-.538.212Zm0-4.875q-.325 0-.537-.213-.213-.212-.213-.537 0-.325.213-.538.212-.212.537-.212h16q.325 0 .538.212.212.213.212.538 0 .325-.212.537-.213.213-.538.213Zm0-4.875q-.325 0-.537-.225-.213-.225-.213-.525 0-.325.213-.537.212-.213.537-.213h16q.325 0 .538.213.212.212.212.537 0 .3-.212.525-.213.225-.538.225Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.star-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='m8.85 17.825 3.15-1.9 3.15 1.925-.825-3.6 2.775-2.4-3.65-.325-1.45-3.4-1.45 3.375-3.65.325 2.775 2.425ZM12 17.7l-3.9 2.325q-.2.125-.425.112-.225-.012-.4-.137-.175-.125-.275-.337-.1-.213-.025-.463L8 14.8l-3.425-2.975q-.2-.175-.25-.4-.05-.225.025-.425.075-.2.238-.338.162-.137.412-.162l4.525-.4L11.3 5.925q.1-.225.288-.338.187-.112.412-.112.225 0 .413.112.187.113.287.338l1.775 4.175 4.525.4q.25.025.413.162.162.138.237.338.075.2.025.425-.05.225-.25.4L16 14.8l1.025 4.4q.075.25-.025.463-.1.212-.275.337-.175.125-.4.137-.225.013-.425-.112Zm0-4.45Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

.star-filled-icon {
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' height='24' width='24' fill='%233f4849'%3E%3Cpath d='m12 17.7-3.9 2.325q-.2.125-.425.112-.225-.012-.4-.137-.175-.125-.275-.337-.1-.213-.025-.463L8 14.8l-3.425-2.975q-.2-.175-.25-.4-.05-.225.025-.425.075-.2.238-.338.162-.137.412-.162l4.525-.4L11.3 5.925q.1-.225.288-.338.187-.112.412-.112.225 0 .413.112.187.113.287.338l1.775 4.175 4.525.4q.25.025.413.162.162.138.237.338.075.2.025.425-.05.225-.25.4L16 14.8l1.025 4.4q.075.25-.025.463-.1.212-.275.337-.175.125-.4.137-.225.013-.425-.112Z'/%3E%3C/svg%3E") no-repeat center center / cover;
    width: 1.5rem;
    height: 1.5rem;
}

Happy coding!
