# Migration `20200617180545-create-contact`

This migration has been generated at 6/17/2020, 6:05:45 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
PRAGMA foreign_keys=OFF;

CREATE TABLE "quaint"."Contact" (
"createdAt" DATE NOT NULL DEFAULT CURRENT_TIMESTAMP ,"email" TEXT NOT NULL  ,"id" INTEGER NOT NULL  PRIMARY KEY AUTOINCREMENT,"message" TEXT NOT NULL  ,"name" TEXT NOT NULL  )

PRAGMA "quaint".foreign_key_check;

PRAGMA foreign_keys=ON;
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200616202623-create-posts..20200617180545-create-contact
--- datamodel.dml
+++ datamodel.dml
@@ -1,17 +1,24 @@
 datasource DS {
   provider = "sqlite"
-  url = "***"
+  url      = env("DATABASE_URL")
 }
 generator client {
   provider      = "prisma-client-js"
   binaryTargets = env("BINARY_TARGET")
 }
-
 model Post {
   id        Int      @id @default(autoincrement())
   title     String
   body      String
   createdAt DateTime @default(now())
-}
+}
+
+model Contact {
+  id        Int @id @default(autoincrement())
+  name      String
+  email     String
+  message   String
+  createdAt DateTime @default(now())
+}
```


