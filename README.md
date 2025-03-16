# Smart Shopping List & Expense Manager

## Project Overview

The **Smart Shopping List & Expense Manager** is a web application designed to help users efficiently manage their grocery shopping and expenses. It enables users to:

- Create and organize shopping lists
- Compare prices from registered markets
- Track spending habits
- Collaborate with family members or housemates

## Technology Stack

- **Backend:** Java, Spring  
- **Frontend:** Angular  
- **Database:** PostgreSQL / MySQL  
- **Hosting:** Netlify/Heroku  

## Team Members & Feature Assignment

### **Team Member 1:** Amina 
- **User Authentication & Profile Management** – Sign up, log in, and manage profiles.
- **Referral & Loyalty System** – Earn rewards for referring friends and accumulating loyalty points.
- **Dark Mode Toggle** – Customize UI with light and dark mode.

### **Team Member 2:** Tarik
- **Shopping List Management & Smart Item Search** – Search for and add items based on availability and pricing.
- **Price Comparison & Intelligent Store Selection** – Compare prices and get smart store recommendations.
- **Favorite Products & Stores** – Mark favorites for quick access and personalized recommendations.

### **Team Member 3:** Pavel
- **Admin Management of Markets, Products & Users** – Manage market, product, and user data via an admin dashboard.
- **Multi-User Sync & Shared Lists** – Sync and manage shared shopping lists.
- **Expense Tracking & Budget Analytics** – Track grocery expenses and generate reports.

## Site Map

![sitemao](https://github.com/Fruerdd/smart-shopping-list-expense-manager-issues/blob/main/sitemap.jpg)


## Mockups

- Visual mockups and wireframes will be designed using Figma.
- Each feature will have an associated wireframe illustrating its UI/UX.
- Mockups will be stored in the `mockups/` folder in the repository.

## Data Source for Markets & Items

Instead of markets being user-managed, the admin will maintain the market and product database. A CSV file (potentially sourced from Kaggle or other datasets) will contain:

- A list of grocery items
- Prices of items across different markets
- Market names and locations

This data will be used to populate and maintain the price comparison functionality.

## Intelligent Shopping List Management

Users can:

- **Search for Items:** Items available will appear under the search bar.
- **Smart Store Selection:** Automatically selects the product from:
  - The cheapest store
  - A preferred store (if set)
  - A favorite store (based on past purchases)
- **Grouped Shopping Logic:** Ensures most items are bought from the same store unless price differences are significant.
- **Manual Store Selection:** Users can override automatic selection.

## Referral & Loyalty System

### **Referral System**
- Users can invite friends via a unique referral code or link.
- Both the referrer and the new user receive rewards upon sign-up and first purchase.
- The system tracks successful referrals.

### **Loyalty Program**
- Users earn points for purchases.
- Points can be redeemed for discounts and exclusive deals.
- Loyalty tiers (Bronze, Silver, Gold) offer increasing rewards.

## API Documentation

### **API Endpoints**

| #  | CRUD   | URL Path                 | Request         | Response         | Description                          |
|----|--------|-------------------------|----------------|----------------|--------------------------------------|
| I.a | Create | `/user/register`         | `UserDto`      | `UserDto`      | Registers a new user.                |
| I.b | Create | `/user/login`            | `AuthDto`      | `AuthResponse` | Authenticates user and returns token.|
| II.a | Create | `/shopping-list`        | `ShoppingListDto` | `ShoppingListDto` | Creates a new shopping list.       |
| II.b | Read   | `/shopping-list/{id}`   | -              | `ShoppingListDto` | Retrieves a shopping list.       |
| II.c | Update | `/shopping-list/{id}`   | `ShoppingListDto` | `ShoppingListDto` | Updates a shopping list.       |
| II.d | Delete | `/shopping-list/{id}`   | -              | -              | Deletes a shopping list.       |
| III.a | Read  | `/price-comparison`      | -              | `List`         | Returns price comparisons.          |
| IV.a | Read   | `/expenses/{userId}`    | -              | `List`         | Retrieves user's expenses.          |
| IV.b | Create | `/expense`              | `ExpenseDto`   | `ExpenseDto`   | Logs a new expense entry.           |
| IV.c | Update | `/expense/{expenseId}`  | `ExpenseDto`   | `ExpenseDto`   | Updates an expense.                 |
| IV.d | Delete | `/expense/{expenseId}`  | -              | -              | Deletes an expense.                 |
| V.a | Create | `/referral/invite`       | `ReferralDto`  | `ReferralResponse` | Sends a referral invitation.      |
| V.b | Read   | `/loyalty/points/{userId}` | -            | `LoyaltyDto`   | Retrieves user loyalty points.      |

### **Data Transfer Objects (DTOs)**

```json
UserDto {
  "id": number,
  "name": string,
  "email": string,
  "password": string
}
```
```json
ShoppingListDto {
  "id": number,
  "userId": number,
  "items": List<ShoppingItemDto>,
  "storePreferences": ["Cheapest", "Favorite"]
}
```
```json
PriceDto {
  "itemId": number,
  "store": string,
  "price": number,
  "lastUpdated": string
}
```
```json
ExpenseDto {
  "id": number,
  "userId": number,
  "amount": number,
  "category": string,
  "date": string,
  "paymentMethod": string
}
```
```json
ReferralDto {
  "id": number,
  "referrerId": number,
  "referredUserId": number,
  "status": string,
  "rewardEarned": number
}
```
```json
LoyaltyDto {
  "userId": number,
  "points": number,
  "tier": string
}
```

## Out of Scope

- **AI-based purchase predictions:** Not included in the initial version.
- **Real-time Store Inventory:** Live stock updates not implemented initially.
- **Mobile App Version:** Initially, the application is web-based.


