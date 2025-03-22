# Supabase CLI Cheat Sheet

This document provides a comprehensive list of Supabase CLI commands and their use cases. Use this as a reference to manage your Supabase projects effectively.

---

## **Supabase CLI Commands**

### **Initialize a Supabase Project**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase init`                  | Initializes a new Supabase project in the current directory.                    |
| `supabase start`                 | Starts the local Supabase stack (database, Auth, Storage, etc.).               |
| `supabase stop`                  | Stops the local Supabase stack.                                                 |

---

### **Database Migrations**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase migration new <name>`  | Creates a new migration file in `supabase/migrations`.                         |
| `supabase migration up`          | Applies all pending migrations to the local database.                           |
| `supabase db reset`              | Wipes the local database and reapplies all migrations from scratch.             |
| `supabase db push`               | Synchronizes the remote database with the local schema.                         |
| `supabase db pull`               | Pulls the schema from the remote database and generates a migration file.       |
| `supabase db dump`               | Creates a backup of the local database schema and data as an SQL file.          |
| `supabase db dump --remote`      | Creates a backup of the remote database schema and data as an SQL file.         |

---

### **Seed Operations**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase db seed`               | Runs the seed script (`supabase/seed.sql`) to populate the local database.      |
| Manually run `seed.sql`          | Use the Supabase SQL Editor or `psql` to run the seed script on the remote DB.  |

---

### **Authentication**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase gen types typescript`  | Generates TypeScript types for your database schema.                           |

---

### **Storage**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase storage`               | Interact with Supabase Storage (e.g., create buckets, upload files).            |

---

### **Secrets Management**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase secrets set <key>=<value>` | Sets environment variables for the local Supabase stack.                      |
| `supabase secrets list`          | Lists all secrets set for the local Supabase stack.                             |

---

### **Edge Functions**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase functions deploy <name>` | Deploys an Edge Function to the remote Supabase project.                      |
| `supabase functions serve`       | Serves Edge Functions locally for testing.                                      |

---

### **Project Management**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase link --project-ref <ref>` | Links your local project to a remote Supabase project.                       |
| `supabase unlink`                | Unlinks your local project from the remote Supabase project.                    |

---

### **Logs and Debugging**
| **Command**                     | **Description**                                                                 |
|----------------------------------|---------------------------------------------------------------------------------|
| `supabase logs`                  | Displays logs for the local Supabase stack.                                     |
| Use Supabase Dashboard           | Check logs in the Supabase Dashboard under the "Logs" section.                  |

---

## **Detailed Scenarios and Commands**

### **1. Database Migrations**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You’ve added a new migration and want to apply it locally. | `supabase migration up`       |
| Your local database is broken, and you want to start fresh. | `supabase db reset`           |
| You’re ready to deploy schema changes to production. | `supabase db push`            |
| You want to test your migrations from scratch.    | `supabase db reset`           |
| You want to synchronize the remote database with your local schema. | `supabase db push`            |
| You want to pull the latest schema from the remote database. | `supabase db pull`            |

---

### **2. Seed Operations**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You want to seed your local database with test data. | `supabase db seed`            |
| You want to seed your remote database with test data. | Manually run `seed.sql`       |

---

### **3. Edge Functions**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You want to deploy an Edge Function to production. | `supabase functions deploy <name>` |
| You want to test an Edge Function locally.        | `supabase functions serve`    |

---

### **4. Storage**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You want to create a new storage bucket.          | `supabase storage create <bucket>` |
| You want to upload files to a storage bucket.     | `supabase storage upload <bucket> <file>` |

---

### **5. Secrets Management**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You want to set environment variables for local development. | `supabase secrets set <key>=<value>` |
| You want to list all secrets.                     | `supabase secrets list`       |

---

### **6. Project Management**
| **Scenario**                                      | **Command to Use**            |
|---------------------------------------------------|-------------------------------|
| You want to link your local project to a remote Supabase project. | `supabase link --project-ref <ref>` |
| You want to unlink your local project from a remote project. | `supabase unlink`             |

---

## **Example Workflow**

1. **Initialize a Project**:
   ```bash
   supabase init
   supabase start