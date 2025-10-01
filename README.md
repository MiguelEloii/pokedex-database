# 🎮 Pokédex Database

A normalized PostgreSQL database project demonstrating database design, SQL proficiency, and QA testing methodologies.

## 📋 Project Overview

Built as part of my transition into Quality Assurance, this project showcases my ability to design relational databases, write complex SQL queries, and apply QA thinking to identify data integrity issues.

## 🎯 Purpose

- Learn database normalization principles
- Practice writing complex SQL queries with JOINs
- Apply QA methodologies (exploratory testing, boundary testing, data validation)
- Build a portfolio piece demonstrating technical SQL skills

## 🛠️ Technologies Used

- **Database:** PostgreSQL 16
- **Tools:** DBeaver
- **Language:** SQL

## 📊 Database Schema

The database consists of 7 interconnected tables:

### Core Tables
- **pokemon** - Basic Pokémon information (id, name, height, weight, legendary status)
- **types** - Master list of all Pokémon types (Fire, Water, Grass, etc.)
- **abilities** - Master list of abilities with descriptions
- **stats** - Individual stat values (HP, Attack, Defense, Sp.Attack, Sp.Defense, Speed)
- **evolutions** - Evolution chains and requirements

### Junction Tables (Many-to-Many Relationships)
- **pokemon_types** - Handles Pokémon with dual types (e.g., Charizard: Fire + Flying)
- **pokemon_abilities** - Connects Pokémon to their abilities, including hidden abilities

## ✨ Key Features

✅ **Proper Normalization** - Data is organized to minimize redundancy and maintain integrity

✅ **Referential Integrity** - Foreign key constraints prevent orphaned records and invalid data

✅ **Many-to-Many Relationships** - Junction tables properly handle complex relationships

✅ **Data Validation** - Constraints ensure data quality (UNIQUE, NOT NULL, CHECK)

✅ **Self-Referencing Tables** - Evolutions table references the pokemon table twice

## 🧪 QA Testing & Findings

Applied exploratory and boundary testing methodologies to identify data integrity issues:

### Bugs Found

**BUG-001: Missing Constraint on Type Slots**
- **Severity:** Medium
- **Issue:** System allowed Pokémon to have more than 2 types (slots > 2)
- **Expected:** Pokémon should only have 1-2 types maximum
- **Root Cause:** Missing CHECK constraint on `pokemon_types.slot` column
- **Fix:** Add `CHECK (slot IN (1, 2))` constraint

### Sample Validation Queries
```sql
