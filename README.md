## Shopify Frontend Developer Junior Test Task

**Objective:** To familiarize yourself with the Shopify Admin, theme code structure, **Git-based development workflow**, and the fundamental concept of Liquid by displaying store data (specifically product information) within a custom section.

**Scenario:** You've been given access to a new Shopify development store and a Git repository containing the theme code. Your goal is to create a simple, static section on the homepage that showcases a "Featured Product." This section will display an image, title, and description of a specific product you'll create. The key is to learn how to access this product data within your theme using Liquid and deploy your changes via Git.

**Deliverables:**

1.  A newly created product in the Shopify Admin.
2.  A new custom section in the theme's Git repository that displays the created product's image, title, and description.
3.  The section deployed to the development store and added to the homepage.
4.  A Git commit containing your changes, pushed to the provided repository.

-----

### **Part 1: Shopify Admin Exploration & Product Creation**

**Task 1.1: Log in to the Shopify Store**

  * **Instruction:** Log in to the provided Shopify development store. (You will be given the store URL and credentials).
  * **Expected Outcome:** You should be in the Shopify Admin dashboard.

**Task 1.2: Create a New Product**

  * **Instruction:**
    1.  Navigate to "Products" in the Shopify Admin.
    2.  Click "Add product."
    3.  Create a new product with the following details:
          * **Title:** "My Awesome Featured Product"
          * **Description:** "This is an amazing product designed to showcase your new Shopify development skills. It's the best of its kind\!"
          * **Image:** Upload any placeholder image (e.g., a stock image, a simple graphic).
          * **Price:** Set a price (e.g., $19.99).
          * Ensure the product is set to "Active" and visible on the "Online Store" sales channel.
  * **Expected Outcome:** A new product, "My Awesome Featured Product," is visible in your product list in the Shopify Admin. Make a note of its **handle** (it's usually the title in lowercase with spaces replaced by hyphens, e.g., `my-awesome-featured-product`).

-----

### **Part 2: Git Workflow, Theme Code, & Introducing Liquid**

**Task 2.1: Clone the Theme Repository & Set Up Local Environment**

  * **Instruction:**
    1.  You will be provided with a Git repository URL (e.g., `https://github.com/your-org/your-shopify-theme.git`).
    2.  Clone the repository to your local machine:
        ```bash
        git clone <repository_url>
        cd <repository_name>
        ```
    3.  Ensure you have [Shopify CLI](https://www.google.com/search?q=https://shopify.dev/docs/apps/tools/cli/install) installed and configured for your store.
    4.  Navigate into your cloned theme directory and connect to your development store:
        ```bash
        shopify theme dev --store=<your-dev-store-name>.myshopify.com # This will open a browser for live preview
        ```
  * **Expected Outcome:** You have the theme code on your local machine, and `shopify theme dev` is running, providing a local development server and live preview.

**Task 2.2: Create a New Section File**

  * **Instruction:**
    1.  Inside your local theme directory, navigate to the `sections` folder.
    2.  Create a new file named `featured-product-section.liquid` within this `sections` directory.
    <!-- end list -->
      * *Self-Correction Note:* If you're using a code editor like VS Code, you can right-click the `sections` folder and choose "New File".
  * **Expected Outcome:** A new file named `featured-product-section.liquid` exists in your local `sections` folder.

**Task 2.3: Implement the Section HTML, CSS, and Basic Liquid**

  * **Instruction:** Open the `featured-product-section.liquid` file you just created and add the following code in small chunks. As you add each chunk, observe how `shopify theme dev` refreshes your browser, but the section won't be visible yet as it's not added to the homepage.

    **Chunk 2.3.1: Basic HTML Structure & Styling**

      * **Code to add:**
        ```html
        <style>
          .featured-product-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 40px 20px;
            background-color: #f8f8f8;
            border-radius: 8px;
            margin: 40px auto;
            max-width: 900px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
          }

          .featured-product-image {
            max-width: 100%;
            height: auto;
            border-radius: 4px;
            margin-bottom: 20px;
          }

          .featured-product-title {
            font-size: 2.5em;
            margin-bottom: 10px;
            color: #333;
          }

          .featured-product-description {
            font-size: 1.1em;
            line-height: 1.6;
            color: #555;
            max-width: 700px;
            margin-bottom: 20px;
          }
        </style>

        <div class="featured-product-container">
          </div>
        ```
      * **Expected Outcome:** Your `featured-product-section.liquid` file now contains the basic HTML structure and CSS for your section.

    **Chunk 2.3.2: Introducing Liquid - Accessing a Product**

      * **Code to add (replace \`\`):**
        ```liquid
        {% assign featured_product = all_products['YOUR_PRODUCT_HANDLE'] %}

        {% if featured_product %}
          {% else %}
          <p>Featured product not found. Please ensure the product handle is correct.</p>
        {% endif %}
        ```
      * **Crucial Step:** **Replace `YOUR_PRODUCT_HANDLE`** with the actual handle of the product you created in Task 1.2 (e.g., `my-awesome-featured-product`).
      * **Explanation of Liquid:**
          * `{% assign featured_product = all_products['YOUR_PRODUCT_HANDLE'] %}`: This is an `assign` tag. It's used to create a new variable (`featured_product`) and assign it a value. Here, we're accessing the `all_products` global object, which holds all products in your store. We're retrieving a specific product by its `handle`.
          * `{% if featured_product %}`: This is an `if` tag, a control flow tag similar to an `if` statement in other programming languages. It checks if the `featured_product` variable has a value (i.e., if a product with that handle was found).
      * **Liquid Docs Link:**
          * [Liquid `assign` tag](https://www.google.com/search?q=%5Bhttps://shopify.dev/docs/api/liquid/tags/assign%5D\(https://shopify.dev/docs/api/liquid/tags/assign\))
          * [Liquid `all_products` object](https://www.google.com/search?q=%5Bhttps://shopify.dev/docs/api/liquid/objects/all_products%5D\(https://shopify.dev/docs/api/liquid/objects/all_products\))
          * [Liquid `if` tag](https://www.google.com/search?q=%5Bhttps://shopify.dev/docs/api/liquid/tags/if%5D\(https://shopify.dev/docs/api/liquid/tags/if\))
      * **Expected Outcome:** Your section now attempts to fetch a product by its handle and includes a basic check if the product is found.

    **Chunk 2.3.3: Displaying Product Image, Title, and Description**

      * **Code to add (replace \`\` inside the `{% if featured_product %}` block):**
        ```liquid
        <img
          src="{{ featured_product.featured_image | image_url: width: 600 }}"
          alt="{{ featured_product.title }}"
          class="featured-product-image"
        >
        <h2 class="featured-product-title">{{ featured_product.title }}</h2>
        <div class="featured-product-description">
          {{ featured_product.description }}
        </div>
        ```
      * **Explanation of Liquid:**
          * `{{ featured_product.featured_image | image_url: width: 600 }}`: This is an *output object*. `featured_product.featured_image` accesses the primary image of the product. The `| image_url: width: 600` part is a *Liquid filter* that processes the image object to output a URL for the image, specifically requesting a version with a width of 600 pixels. Filters are used to modify the output of Liquid objects.
          * `{{ featured_product.title }}`: This outputs the `title` property of your `featured_product`.
          * `{{ featured_product.description }}`: This outputs the `description` property of your `featured_product`.
      * **Liquid Docs Link:**
          * [Liquid `product` object (specifically `product.title`, `product.description`, `product.featured_image`)](https://www.google.com/search?q=%5Bhttps://shopify.dev/docs/api/liquid/objects/product%5D\(https://shopify.dev/docs/api/liquid/objects/product\))
          * [Liquid `image_url` filter](https://www.google.com/search?q=%5Bhttps://shopify.dev/docs/api/liquid/filters/image_url%5D\(https://shopify.dev/docs/api/liquid/filters/image_url\))
      * **Expected Outcome:** Your section now dynamically displays the image, title, and description of your chosen product using Liquid.

    **Chunk 2.3.4: Adding Section Schema (for Theme Customizer)**

      * **Code to add (at the very bottom of `featured-product-section.liquid`):**
        ```liquid
        {% schema %}
        {
          "name": "Featured Product Section",
          "settings": [
            {
              "type": "text",
              "id": "product_handle",
              "label": "Product Handle",
              "info": "Enter the handle of the product to feature (e.g., 'my-awesome-featured-product')",
              "default": "my-awesome-featured-product"
            }
          ],
          "presets": [
            {
              "name": "Featured Product",
              "category": "Custom Sections"
            }
          ]
        }
        {% endschema %}
        ```
      * **Explanation of Liquid Schema:** The `{% schema %}` block is not Liquid itself, but a JSON structure that Shopify uses to define editable settings for your section within the Theme Customizer. This allows merchants to easily change the product handle without touching the code.
      * **Shopify Docs Link:**
          * [Shopify Theme Sections](https://shopify.dev/docs/themes/architecture/sections) (This page explains the `{% schema %}` block in detail).
      * **Expected Outcome:** Your section is now properly defined for the Theme Customizer.

**Task 2.4: Deploy Changes & Add the New Section to the Homepage**

  * **Instruction:**
    1.  **Stop** your `shopify theme dev` process (usually by pressing `Ctrl + C` in your terminal).
    2.  **Deploy your changes** to the development store. This will push your new section file to the live theme:
        ```bash
        shopify theme push
        ```
          * *Note:* If prompted, select the correct theme to push to (it should be the one you're currently working on in the dev store).
    3.  Go back to the Shopify Admin.
    4.  Navigate to "Online Store" \> "Themes."
    5.  Find the theme you just pushed to (it should have a recent modification date) and click the "Customize" button. This will open the Theme Editor.
    6.  On the left sidebar, click "Add section."
    7.  Find your newly created "Featured Product" section under "Custom Sections" and click to add it to your homepage.
    8.  You can drag and drop the section to a desired position on the page.
    9.  Click "Save" in the top right corner.
  * **Expected Outcome:** Your Shopify store's homepage now displays the "Featured Product Section" with the image, title, and description of the product you created in Part 1.

**Task 2.5: Commit and Push Your Changes**

  * **Instruction:**
    1.  In your terminal, ensure you are in the root directory of your cloned theme.
    2.  Check the status of your changes:
        ```bash
        git status
        ```
        You should see `sections/featured-product-section.liquid` listed as a new file.
    3.  Stage your changes:
        ```bash
        git add sections/featured-product-section.liquid
        ```
    4.  Commit your changes:
        ```bash
        git commit -m "feat: Add featured product section with basic Liquid"
        ```
    5.  Push your changes to the remote repository:
        ```bash
        git push origin <your-branch-name> # Replace <your-branch-name> with your current branch, often 'main' or 'master'
        ```
  * **Expected Outcome:** Your changes are committed to your local Git history and pushed to the remote repository, making your work visible to others.

-----

### **Evaluation Criteria:**

  * **Successful Login:** Can the developer successfully log into the Shopify Admin?
  * **Product Creation:** Is the product created correctly with the specified details?
  * **Git Workflow:**
      * Can the developer clone the repo?
      * Can they use `shopify theme dev` to run locally?
      * Can they use `shopify theme push` to deploy changes?
      * Are the changes committed and pushed correctly to the Git repository?
  * **Section File Creation:** Is the `featured-product-section.liquid` file correctly created in the `sections` directory of the cloned theme?
  * **Liquid Implementation:** Is the Liquid code correctly used to fetch and display the product data (image, title, description)? This means the correct product handle is used, and the Liquid objects and filters are applied.
  * **Frontend Display:** Does the section appear on the homepage with the correct product information and basic styling after deployment?
  * **Understanding of Liquid Basics:** Can the developer articulate *why* they used `all_products` and `featured_product.title` (or similar objects) and what they represent? This can be a brief verbal explanation after the task is completed.
