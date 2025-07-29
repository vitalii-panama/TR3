## Shopify Frontend Developer Junior Test Task - Part 2

**Objective:** Build upon the foundation from Part 1 by adding product options, implementing a functional product form with option selection, and applying basic styling to create a complete product showcase section.

**Scenario:** Now that you have a basic featured product section displaying static product information, you'll enhance it to include product variants (options like size, color, etc.), add a functional "Add to Cart" form with option selection, and apply simple styling to make it functional and presentable.

**Deliverables:**

1. Product variants/options added to the existing product in Shopify Admin
2. Enhanced section with a working product form that includes option selectors
3. Functional "Add to Cart" button that submits the form
4. Basic styling that looks clean and functional
5. Git commit containing all changes, pushed to the repository

---

### **Part 2.1: Adding Product Options in Shopify Admin**

**Task 2.1.1: Access Your Existing Product**

- **Instruction:**
  1. You already have access to the Shopify development store
  2. Navigate to "Products" in the Shopify Admin
  3. Find and click on "My Awesome Featured Product" (the product you created in Part 1)

**Task 2.1.2: Add Product Variants/Options**

- **Instruction:**

  1. In the product edit page, scroll down to the "Variants" section
  2. Add at least two product options (e.g., Size and Color)
  3. For Size option, add variants like: Small, Medium, Large
  4. For Color option, add variants like: Red, Blue, Green
  5. Ensure each variant combination has a price set
  6. Make sure all variants are set to "Active" and available for the "Online Store" sales channel
  7. Save the product changes

- **Expected Outcome:** Your product now has multiple variants with different options that customers can select from.

---

### **Part 2.2: Implementing Product Form with Option Selection**

**Task 2.2.1: Enhance the Section Structure**

- **Instruction:**
  1. Open your existing `featured-product-section.liquid` file
  2. Modify the section to include a product form structure
  3. Add form elements that will handle the product options and submission

**Task 2.2.2: Add Product Option Selectors**

- **Instruction:**
  1. Implement option selectors (dropdowns or radio buttons) for each product option (Size, Color)
  2. Ensure the selectors dynamically populate with the available variants from your product
  3. Add proper labels and accessibility attributes for each selector
  4. Include a quantity selector for the product

**Task 2.2.3: Implement Add to Cart Functionality**

- **Instruction:**
  1. Add a submit button labeled "Add to Cart"
  2. Ensure the form submits to the correct Shopify cart endpoint
  3. Include all necessary form fields for Shopify's cart functionality
  4. Add proper form validation and error handling

**Task 2.2.4: Handle Variant Selection**

- **Instruction:**
  1. Ensure the form properly handles variant selection using Liquid
  2. Make sure the form data is correctly structured for Shopify's cart functionality

### **Evaluation Criteria:**

- **Product Options Implementation:** Are the product variants properly displayed and selectable in the form?
- **Form Functionality:** Does the "Add to Cart" button work correctly and add the selected variant to the cart?

---

### **Learning Objectives:**

- Understanding Shopify product variants and how to access them in Liquid
- Implementing functional forms in Shopify themes
- Working with Shopify's cart functionality
- Creating functional forms
- Handling form submissions with Liquid
- Working with Shopify's form structure

This part builds upon the foundational knowledge from Part 1 and introduces more advanced concepts like form handling, variant management, and working with Shopify's cart functionality using only HTML, CSS, and Liquid.
