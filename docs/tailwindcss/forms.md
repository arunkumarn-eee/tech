# Forms

## Floating label with outline

```html
<div class="relative">
    <input 
    type="text" 
    id="floating_outlined" 
    class="block px-2.5 pb-2.5 pt-4 w-full 
    text-sm text-gray-900 bg-transparent rounded-lg 
    border-1 border-gray-300 appearance-none 
    dark:text-white dark:border-gray-600 dark:focus:border-blue-500 
    focus:outline-none focus:ring-0 focus:border-blue-600 
    peer" 
    placeholder=" " />

    <label 
    for="floating_outlined" 
    class="absolute 
    text-sm text-gray-500 left-1 top-2 z-10
    bg-white dark:text-gray-400 dark:bg-gray-900 px-2 
    duration-300 transform -translate-y-4 scale-75  origin-[0]  
    peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500
    peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4
    peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 
    peer-placeholder-shown:top-1/2  ">
    Floating outlined
    </label>
</div>
```

!!! info

    For Phone number
    ```html
    <input type="tel" id="phone" pattern="[6-9]{1}[0-9]{9}" />
    ```


=== "Label"

    ```html
    <div class="relative">
        <input 
        type="text" 
        id="floating_outlined" 
        class="block px-2.5 pb-2.5 pt-4 w-full 
        text-sm text-gray-900 bg-transparent rounded-lg 
        border-1 border-gray-300 appearance-none 
        dark:text-white dark:border-gray-600 dark:focus:border-blue-500 
        focus:outline-none focus:ring-0 focus:border-blue-600 
        peer" 
        placeholder=" " />

        <label 
        for="floating_outlined" 
        class="absolute 
        text-sm text-gray-500 left-1 top-2 z-10
        bg-white dark:text-gray-400 dark:bg-gray-900 px-2 
        duration-300 transform -translate-y-4 scale-75  origin-[0]  
        peer-focus:px-2 peer-focus:text-blue-600 peer-focus:dark:text-blue-500
        peer-focus:top-2 peer-focus:scale-75 peer-focus:-translate-y-4
        peer-placeholder-shown:scale-100 peer-placeholder-shown:-translate-y-1/2 
        peer-placeholder-shown:top-1/2  ">
        Floating outlined
        </label>
    </div>
    ```

=== "Telephone"

    ```html title="telephone"

    <div class="relative m-4">
        <input required type="tel" id="phone" pattern="[6-9]{1}[0-9]{9}" class="peer block w-full appearance-none rounded-lg border-2 border-gray-300 bg-transparent px-2.5 pb-2.5 pt-4 text-sm text-gray-900 focus:border-blue-600 focus:outline-none focus:ring-0 dark:border-gray-600 dark:text-white dark:focus:border-blue-500" placeholder=" " />

        <label for="phone" class="absolute left-1 top-2 z-10 origin-[0] -translate-y-4 scale-75 transform bg-white px-2 text-sm text-gray-500 duration-300 peer-placeholder-shown:top-1/2 peer-placeholder-shown:-translate-y-1/2 peer-placeholder-shown:scale-100 peer-focus:top-2 peer-focus:-translate-y-4 peer-focus:scale-75 peer-focus:px-2 peer-focus:text-blue-600 dark:bg-gray-900 dark:text-gray-400 peer-focus:dark:text-blue-500"> Phone </label>
    </div>
    ```

