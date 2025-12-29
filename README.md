# ShopStream Backend 🛒💻

**ShopStream** is a modern e-commerce web application built with **Angular** and **Node.js**. The platform allows users to browse, search, and purchase products seamlessl, providing a smooth and responsive user experience.

Key features include:
*   User authentication & authorization
*   Product browsing and filtering
*   Shopping cart management
*   Secure checkout process
*   Admin functionalities for managing products and orders

---

## 🚀 Getting Started

### Prerequisites
*   Node.js (v14+ recommended)
*   MongoDB (Local or Atlas)

### Installation

1.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd ShopStream-Backend
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Environment Configuration:**
    A `.env` file has been configured for you. Ensure the following variables are set (defaults provided):
    ```env
    PORT=3000
    MONGO_URI=mongodb://localhost:27017/shopstream
    JWT_REFRESH_SECRET=19781225
    JWT_ACCESS_SECRET=19781225
    ...
    ```

4.  **Start the Server:**
    ```bash
    npm start
    ```

---

## 🛠️ Technology Stack & Enhancements

We have enhanced the original codebase to improve performance, security, and maintainability.

### Core Stack
*   **Runtime**: Node.js
*   **Framework**: Express.js
*   **Database**: MongoDB (Mongoose)
*   **Security**: `helmet`, `express-rate-limit`, `bcrypt`, `jsonwebtoken`
*   **Performance**: `compression`

### 🔍 Algorithmic Optimizations

#### 1. N+1 Query Elimination (Order Placement)
*   **Problem**: Fetching menu items for an order generated **N** separate database calls (one per item).
*   **Solution**: Implemented batch fetching using MongoDB's `$in` operator.
*   **Impact**: Reduced database round-trips from **O(N)** to **O(1)**.

#### 2. O(1) Validation Lookup
*   **Problem**: Validating requested items against fetched items using nested loops resulted in **O(N²)** complexity.
*   **Solution**: Indexed fetched items in a **Hash Map** by ID.
*   **Impact**: Validation lookup time is now **O(1)**.

#### 3. Data Integrity
*   **Solution**: Used `Sets` to enforce unique variation sizes during validation.
*   **Impact**: Ensures data consistency with **O(N)** efficiency.

#### 4. Read Performance
*   **Solution**: Applied Mongoose `.lean()` to read-only queries.
*   **Impact**: Returns plain JavaScript objects instead of heavy Mongoose documents, significantly reducing memory usage and parsing time.

---

## 📦 Project Dependencies

A comprehensive breakdown of the packages used in this project.

### Core Framework & Utilities
| Package | Purpose | Impact |
| :--- | :--- | :--- |
| **express** | Web Framework | **Critical**. Handles routing and middleware. |
| **dotenv** | Configuration | **Critical**. Manages environment secrets detailed above. |
| **cors** | Security/Networking | **High**. Enables frontend-backend communication. |
| **socket.io** | Real-Time | **High**. Powers live updates for orders/chat. |

### Database & Storage
| Package | Purpose | Impact |
| :--- | :--- | :--- |
| **mongoose** | ODM | **Critical**. Schema enforcement and DB interaction. |
| **mongoose-paginate-v2** | Pagination | **High**. Efficient data loading for large lists. |
| **cloudinary** | Media Storage | **High**. Optimized image hosting and CDN delivery. |

### Security
| Package | Purpose | Impact |
| :--- | :--- | :--- |
| **helmet** | HTTP Security | **High**. Sets secure HTTP headers to prevent attacks. |
| **express-rate-limit** | DoS Protection | **High**. Throttles abusive request traffic. |
| **bcrypt** | Password Hashing | **Critical**. Encrypts user passwords. |
| **jsonwebtoken** | Auth Tokens | **Critical**. Stateless authentication. |
| **express-validator** | Input Validation | **High**. Sanitizes incoming request data. |

### Optimization
| Package | Purpose | Impact |
| :--- | :--- | :--- |
| **compression** | Response Size | **Medium**. Gzip compression for faster responses. |
| **winston** | Logging | **Medium**. Structured logging for debugging. |

### External Services
| Package | Purpose | Impact |
| :--- | :--- | :--- |
| **stripe** | Payments | **High**. Secure payment processing. |
| **nodemailer** | Emailing | **High**. Transactional emails. |

---

## 🛡️ License

This project is licensed under the ISC License.
