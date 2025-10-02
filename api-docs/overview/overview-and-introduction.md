# Virtualstock API - Overview and Introduction

## What is Virtualstock?

Virtualstock is a modular SaaS platform that sits between the retailer and their suppliers.

Suppliers could be manufacturers, distributors, vendors or the retailer's own warehouses or store network. In most cases these suppliers are fulfilling dropship or marketplace orders for their client retailers.

While Virtualstock has a range of modules and features, it has been predominantly deployed as a Dropship Solution.

Virtualstock allows the supplier to efficiently share up-to-date order status, delivery status and stock availability information. Virtualstock also has Invoicing and Price Management modules.

In addition, Virtualstock can be used for rich product induction - where the supplier's product data is validated against the retailer's data model, before it is published to the retailer's systems.

## Purpose of the APIs

The purpose of the Virtualstock's APIs are to enable Retailers and Suppliers to create and manage their suppliers, products, stock availability, orders and order status.

## Linnworks Integration

Please note that Linnworks has a reusable connector to Virtualstock, so if you are a customer of Linnworks already you can instantly configure the integration and you don't need to do any bespoke integration. If you are not a customer of Linnworks already, but you sell through multiple channels and would be interested in having a system where you can centralise your stock and order management, automatically into all your channels including any Virtualstock customers, please see here for more info:

https://www.linnworks.com/connect/lw-virtualstock-emea

## Getting Started

In order to begin using this API, you should first have been set up and have been provided with at least a test supplier have credentials for the API.

If you want to verify API calls via Postman, you can acquire the Postman pack here. See the "Run in postman" button at the top right of this page.

## Breaking Change Policy

As our APIs evolve, we will make reasonable efforts to notify you of breaking changes in advance with sufficient time to adapt to these changes.

**Important!** Review this guide carefully to understand what kind of changes we consider to be breaking and non-breaking, and how to ensure that your application can adapt automatically to any change we categorise as non-breaking.

### Definition of Breaking Changes

A breaking change is a change that may require you to make changes to your application in order to avoid disruption to your integration. The following are examples of changes we consider breaking:

- Changes to existing permission definitions
- Removal of an allowed parameter, request field or response field
- Addition of a required parameter or request field without default values
- Changes to the intended functionality of an endpoint. For example, if a DELETE request previously used to archive the resource but now hard deletes the resource.
- Introduction of a new validation

### Definition of Non-Breaking Changes

A non-breaking change is a change that you can adapt to at your own discretion and pace without disruption. In most cases, we will communicate non-breaking changes after they are already made. Ensure that your application is designed to be able to handle the following types of non-breaking changes without prior notice:

- Addition of new endpoints
- Addition of new methods to existing endpoints
- New fields in responses
- New optional request fields or parameters
- New required request fields that have default values
- Addition of a new value returned for an existing text field
- Changes to the order of fields returned within a response
- Addition of an optional request header
- Removal of redundant request header
- Changes to the length of data returned within a field
- Changes to the overall response size
- Changes to error messages. We do not recommend parsing error messages to perform business logic. Instead, you should only rely on HTTP response codes and error codes.
- Fixes to HTTP response codes and error codes from incorrect code to correct code

## Environment

- **Sandbox API Base URL**: `https://api.sandbox.virtualstock.com`
- **Production API Base URL**: `https://api.virtualstock.com` (implied)
