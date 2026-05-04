# 🚀 Getting started with Strapi

Strapi comes with a full featured [Command Line Interface](https://docs.strapi.io/dev-docs/cli) (CLI) which lets you scaffold and manage your project in seconds.

### `develop`

Start your Strapi application with autoReload enabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-develop)

```
npm run develop
# or
yarn develop
```

### `start`

Start your Strapi application with autoReload disabled. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-start)

```
npm run start
# or
yarn start
```

### `build`

Build your admin panel. [Learn more](https://docs.strapi.io/dev-docs/cli#strapi-build)

```
npm run build
# or
yarn build
```

## ⚙️ Deployment

Strapi gives you many possible deployment options for your project including [Strapi Cloud](https://cloud.strapi.io). Browse the [deployment section of the documentation](https://docs.strapi.io/dev-docs/deployment) to find the best solution for your use case.

```
yarn strapi deploy
```

## 📚 Learn more

- [Resource center](https://strapi.io/resource-center) - Strapi resource center.
- [Strapi documentation](https://docs.strapi.io) - Official Strapi documentation.
- [Strapi tutorials](https://strapi.io/tutorials) - List of tutorials made by the core team and the community.
- [Strapi blog](https://strapi.io/blog) - Official Strapi blog containing articles made by the Strapi team and the community.
- [Changelog](https://strapi.io/changelog) - Find out about the Strapi product updates, new features and general improvements.

Feel free to check out the [Strapi GitHub repository](https://github.com/strapi/strapi). Your feedback and contributions are welcome!

## ✨ Community

- [Discord](https://discord.strapi.io) - Come chat with the Strapi community including the core team.
- [Forum](https://forum.strapi.io/) - Place to discuss, ask questions and find answers, show your Strapi project and get feedback or just talk with other Community members.
- [Awesome Strapi](https://github.com/strapi/awesome-strapi) - A curated list of awesome things related to Strapi.

---

<sub>🤫 Psst! [Strapi is hiring](https://strapi.io/careers).</sub>

## Community management setup (zone-wise)

This project now includes two content-types for a community app:

- **Zone**: master list of zones (for example: North Zone, East Zone).
- **Member**: families/members linked to one zone.

### Suggested admin role model

In Strapi Admin (`Settings -> Administration Panel -> Roles`), create these roles:

1. **Super Admin**
   - Full access.
   - Only this role should have create/update/delete permission for **Zone**.
2. **Zonal Admin**
   - Read Zone.
   - Create/update/read Member (scope by zone using review workflow or custom policy if needed).
3. **Staff**
   - Read Zone.
   - Read/create Member (optional update based on your process).

> Note: Strapi RBAC can restrict by content-type action. Zone-level row filtering is typically implemented with custom policies/controllers.

### Field mapping from your sample sheet

- `HEAD OF THE FAMILY NAME` -> `headOfFamilyName`
- `CONTACT NO` -> `contactNumber`
- `BLOOD GROUP` (head) -> `headBloodGroup`
- `DOB` -> `headDob`
- `SPOUSE NAME` -> `spouseName`
- `BLOOD GROUP` (spouse) -> `spouseBloodGroup`
- `KIDS NAMES` -> `kidsNames`
- `BLOOD GROUP` (kids) -> `kidsBloodGroups`
- `ANNIVERSARY` -> `anniversary`
- `EMAIL ID` -> `email`
- `ADDRESS` -> `address`
- Zone assignment -> `zone`

### Import suggestion

Use the Strapi Import/Export plugin or CSV import plugin to bulk upload members.
Before import:

- Create zone records first (by Super Admin).
- Normalize date values to `YYYY-MM-DD`.
- Use one zone column in the CSV to map each member to the zone relation.
