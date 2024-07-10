---

# MySQL Advanced Scripts

This repository contains SQL scripts that demonstrate various advanced MySQL functionalities and practices.

## Table of Contents

1. **0-uniq_users.sql**
   - Creates a table `users` with unique email constraint.
   - Attributes: `id`, `email`, `name`.
   - Ensures email uniqueness to prevent duplicates.

2. **1-country_users.sql**
   - Creates a table `users` with country enumeration.
   - Attributes: `id`, `email`, `name`, `country`.
   - Enforces country values (`US`, `CO`, `TN`) with default `US`.

3. **2-fans.sql**
   - Ranks metal bands by fan count based on origin.
   - Utilizes imported table `metal_bands`.

4. **3-glam_rock.sql**
   - Lists glam rock bands ranked by longevity.
   - Computes lifespan using `formed` and `split`.

5. **4-store.sql**
   - Implements trigger to decrease item quantity on order creation.
   - Tables: `items`, `orders`.

6. **5-valid_email.sql**
   - Implements trigger to validate and reset `valid_email` attribute.
   - Table: `users`.

7. **6-bonus.sql**
   - Creates stored procedure `AddBonus` to add corrections for students.
   - Tables: `corrections`, `users`, `projects`.

8. **7-average_score.sql**
   - Creates stored procedure `ComputeAverageScoreForUser` to compute and store average scores for students.
   - Tables: `corrections`, `users`, `projects`.

9. **8-index_my_names.sql**
   - Creates index `idx_name_first` on `names` table for improved search performance.
   - Table: `names`.

10. **9-index_name_score.sql**
    - Creates index `idx_name_first_score` on `names` table for combined name and score search optimization.
    - Table: `names`.

11. **10-safe_divide.sql**
    - Defines function `SafeDiv` to safely divide two numbers, returning 0 if denominator is 0.
    - Table: `numbers`.

## Installation and Usage

- Clone the repository: `git clone https://github.com/your_username/alx-backend-storage.git`
- Execute scripts directly on any MySQL database.
- Ensure appropriate permissions and database setup before execution.

## Notes

- Each script is designed to be portable and executable on any MySQL database instance.
- Check each script's README within its directory for specific usage instructions and context.
- Contributions and improvements are welcome via pull requests.

---
