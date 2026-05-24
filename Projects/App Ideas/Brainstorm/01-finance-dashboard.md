---
title: Finance Dashboard
number: "01"
status: active
tags: [projects, coding, web-app, finance]
created: 2025-04-11
---

# 01. Finance Dashboard

## Overview
A personal finance web app that tracks income, expenses, and investments. Built with Next.js and SQL, using Google OAuth for authentication.

## Goals
- Import and consolidate bank transaction data from ANZ accounts
- Detect and flag duplicate transactions on upload
- Visualise spending and income through a clean dashboard
- Track investments alongside everyday transactions

## Features
- CSV upload with a preview and duplicate detection before committing
- Unique transaction IDs to prevent re-importing the same data
- Editable transactions post-upload (category, amount, notes)
- Ability to manually link related transactions (e.g. group golf payment + repayments)
- Dashboard showing top 10 expenses, top 10 income, and investment section
- Left-hand month/year selector with an "All Time" option
- Settings tab with upload history (file name, timestamp, new rows detected)
- User-generated categories and subcategories

## Tech Stack
- Next.js + SQL (online-only)
- Google OAuth
- Web + Mobile

## Database Schema
- Users — uuid, name, email, auth token
- Transactions — uuid, user_uuid, date, type, category, subcategory, notes, amount, unique_id, linked_transaction_id, account, manually_added
- Uploads — uuid, user_uuid, file_name, upload_time, new_rows_detected
- LinkedTransactions — transaction_1_id, transaction_2_id, link_type
- Categories — id, name, subcategory, user_uuid

## Status
- [ ] Finalise database schema
- [ ] Build Google OAuth and user table
- [ ] Create CSV upload parser
- [ ] Implement duplicate detection
- [ ] Build manual review interface for uploads
- [ ] Set up dashboard components
- [ ] Add transaction linking system
- [ ] Create settings tab
- [ ] Deploy to web

## Links
- [Google Drive Folder](https://drive.google.com/drive/folders/1nHdAeC34eLqZ3cTd-BAKG3Vu6P37JZbe)
