## Essentail Tools

1. If you are using Windows install `Chocolatey` using the Powershell terminal if you haven’t installed it yet. Make sure to open or `run as administrator` the PowerShell.

   To check if `Chocolatey` is already installed in your device run this command

   ```
   choco
   ```

   Visit this `Chocolatey` website to know more https://chocolatey.org/

2. Install `themekit` from Shopify by running this command.
   ```
   choco install themekit
   ```

## Creating Development Store on Shopify

1. Create an account or Login to `Shopify` by visiting https://shopify.dev/.
2. After creating an account hover or go to `Stores` at the sidebar. click `Add store` button and select `Create development store`.
3. Fill up the following form.

## Creating a Theme Password

1. Login to your `Development Store`.
2. Click or select `Apps` on the sidebar, then from the search bar, select `App and sales channel setting`.
3. After selecting `App and sales channel setting`, click the `Shopify App Store` and search for `Theme Access`
4. Click the install button.
5. After installing, click the `Create password` button.
6. Fill out the form and click the `Create password` button at the bottom.
7. Go to the email account you used while filling out the form.
8. Click the `Get Password` button.
9. You will be redirected to another page where you can see the `Show password` button.

   > **Note:** The Password will be shown only once. Once you close it, you can't see it anymore.

## Creating a Shopify Theme Project

1. Create a folder where you want to create your project or `Shopify Theme`
2. Open the folder using your IDE of choice.
3. Run the following command in your terminal
   ```
   theme new --password=<password_generated_from_theme_access> --store=<path>.myshopify.com --name=<project_name>
   ```
4. Verify the creation:
   1. Go to your development store.
   2. Click or select `Online Store` on the sidebar.
   3. Check if the `Shopify Theme` you just created is listed.

## File Structure

<details>
<summary><strong>assest folder</strong></summary>
Contains all the assets (images, logos, css, script) of the theme.
</details>

<details>
<summary><strong>config folder</strong></summary>

Contains the settings of the `Shopify Theme`.

> **settings_data.json**
>
> > Add some text description here.

> **settings_schema.json**
>
> > Allows you to customize the store's theme, including background color, background image, text color and more.

</details>

<details>
<summary><strong>layout folder</strong></summary>

Contains the `theme.liquid` file. Place every element you want to render or display inside this template file.

</details>

<details>
<summary><strong>locales folder</strong></summary>

This is where you create translations for your `Shopify Theme`.

</details>
<details>
<summary><strong>templates folder</strong></summary>

This is where you create or manage your template files for your pages. Please take note that only `.liquid` files are allowed in this folder.

> **customers folder**
>
> > Contains the information of the customer.

> **404.liquid**
>
> > Displays a page that customers are taken to if they visit an invalid page or URL.

> **article.liquid**
>
> > Displays a blog article or blog post.

> **blog.liquid**
>
> > Displays the list of blogs or articles of your store.

> **cart.liquid**
>
> > Displays items in a customer's cart. This is also the page where the customer proceeds to checkout.

> **collection.liquid** | **collection.list.liquid**
>
> > Displays products within a product collection, such as a variety of `shoes` inside a `Shoes Collection`.

> **gift_card.liquid**
>
> > Displays gift card(s) issued to a customer upon purchase.

> **index.liquid**
>
> > Displays the `home` page of your `Shopify Store`.

> **list-collections.liquid**
>
> > Displays the list of collection inside your `Shopify Store`.

> **page.contact.liquid**
>
> > Displays the contact page of your `Shopify Store`.

> **page.liquid**
>
> > Displays pages of your `Shopify Store`, such as `About Us`

> **product.liquid**
>
> > Displays the detailed page of an individual product. This is also where you find the `Add to cart` button, `Buy now` button, and more.

> **search**
>
> > Displays the search results of the storefront.

</details>

### Deployment

To deploy any changes you made from your `Shopify Store` run this command.

```
theme deploy --allow-live
```

```
theme watch --allow-live
```

> **Note:** Publish your `Shopify Theme` to see changes you made.

## Deprecated

1. The `{{ content_for_index }}` object is no longer fuctional. This means that the `Add section` button will not appear in the customize section even if `{{ content_for_index }}` is used in the `index.liquid` file.

   ### Steps to Enable `Add section` Functionality

   To restore the `Add section` functionality, follow these steps:

   1. Rename or delete the `index.liquid` file:
      - Locate the `index.liquid` file in your project directory.
      - Rename it to something else (e.g., `index-deprecated.liquid`) or delete it entirely.
   2. Create a new `index.json` file.
      - In the same directory where the `index.liquid` file was located, create a new file named `index.json`.
   3. Create a json object with the following keys. `name`, `section`, and `order`.

      <details>
      <summary><strong>name</strong></summary>

      `name` key specifies the name of the object.

      </details>

      <details>
      <summary><strong>section</strong></summary>

      `section` key contains an object that defines the sections you want to display in the `Add section` button.

      </details>

      <details>
      <summary><strong>order</strong></summary>

      `order` key is an array that specifies the order of the keys in the `section` object.

      </details>

      #### Example Structure

      Here's an example structure of the `index.json` file:

      ```
      {
         "name": "Home page",
         "sections": {
         "hero-template" : {
                  "type": "hero"
               }
            },
         "order": ["hero-template"]
      }
      ```

## 13 Form Types

1. `{% form 'active_customer_password' %}`
2. `{% form 'contact' %}`
3. `{% form 'currency' %}`
4. `{% form 'customer' %}`
5. `{% form 'create_customer' %}`
6. `{% form 'customer_address' %}`
7. `{% form 'customer_login' %}`
8. `{% form 'guest_login' %}`
9. `{% form 'new_comment' %}`
10. `{% form 'product' %}`
11. `{% form 'recover_customer_password' %}`
12. `{% form 'reset_customer_password' %}`
13. `{% form 'storefront_password' %}`