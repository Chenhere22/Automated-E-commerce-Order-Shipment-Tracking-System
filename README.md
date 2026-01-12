# Automated-E-commerce-Order-Shipment-Tracking-System
for Multi-Vendor Cosmetics Procurement

Overview

This project implements an automated system to track, monitor and manage online procurement orders from multiple cosmetics suppliers (e.g. Parfumdreams, Flaconi, CosmeticExpress).

The system consolidates order confirmations, shipment data and website-only tracking information into a single operational dashboard and automatically triggers supplier follow-ups for delayed shipments.

It is designed for small and medium-sized trading companies that source from many online vendors and need reliable visibility into their logistics flow without a full ERP integration.

Business Problem

Online B2C cosmetics shops are optimized for individual consumers, not for B2B procurement.
Typical problems include:

Tracking numbers are often sent by email or only visible inside supplier portals

Different vendors use different logistics providers (DHL, DPD, Hermes, etc.)

Order and shipment information is fragmented across inboxes and websites

Delayed shipments must be manually detected and followed up

No consolidated view of order status exists

This results in:

Lost or delayed shipments

Manual tracking work

Missed re-ordering signals

Slow customer fulfillment

Solution

This system creates a centralized, automated tracking and escalation layer on top of existing e-commerce suppliers without requiring direct API integrations.

It combines:

Email-based order and shipment parsing

Website-based tracking extraction (RPA / browser automation)

A unified operational data layer (Excel / Google Sheets / Database)

Automated exception handling (delayed shipment reminders)

System Architecture
Online Shops (Parfumdreams, Flaconi, CosmeticExpress)
            ↓
Order & Shipping Emails
            ↓
Microsoft Exchange / Outlook Inbox
            ↓
Email Parser (Graph API / IMAP / Script)
            ↓
Central Order Table (Excel / Google Sheets / DB)
            ↓
Website Scraper / RPA (Power Automate Desktop / Playwright)
            ↓
Tracking Numbers & Status
            ↓
Unified Logistics Dashboard
            ↓
Delay Detection Rules
            ↓
Automated Supplier Follow-up Emails

Key Features
1) Multi-Vendor Order Intake

Automatically extracts:

Order ID

Shop name

Order date

from incoming order confirmation emails.

2) Shipment & Tracking Capture

Supports two data sources:

A) Email-based
If a vendor sends a shipping confirmation email, the system extracts:

Tracking number

Carrier (DHL, DPD, UPS, etc.)

B) Website-based (RPA)
For vendors where tracking is only available in the web portal (e.g. Parfumdreams, Flaconi, CosmeticExpress):

The system logs in automatically

Navigates to order history

Scrapes shipment status and tracking numbers

3) Central Order Database

All orders are stored in a structured table:

Order ID	Vendor	Order Date	Tracking	Carrier	Status	Days Open	Chased

This creates a single source of truth for all procurement logistics.

4) Automated Delay Detection

Rules such as:

If Tracking is empty AND Order age ≥ 2 days

automatically flag orders as delayed.

5) Automated Supplier Follow-Ups

For delayed orders, the system automatically sends:

Polite status-check emails to each supplier

Prevents duplicate reminders by tracking follow-up history

This removes the need for manual chasing.

Technologies

Microsoft Exchange / Outlook (email source)

Power Automate Desktop or Playwright (Python) for web portal extraction

Excel / Google Sheets / SQLite as operational data store

Python / Apps Script for parsing, validation and automation

Windows Task Scheduler for scheduling and unattended execution

Business Impact

This system enables:

Real-time visibility across all suppliers

Faster detection of shipment delays

Reduced manual tracking workload

Higher fulfillment reliability

Data-driven procurement decisions

It converts a fragmented, manual purchasing workflow into a scalable, process-driven logistics operation.

Use Cases

Multi-vendor cosmetics trading companies

Drop-shipping operations

E-commerce resellers

Small import/export businesses

Future Extensions

Power BI / Tableau dashboard

Vendor performance analytics

Inventory forecasting

API-based carrier integration

ERP synchronization
