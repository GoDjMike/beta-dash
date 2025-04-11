# BetaDash

A full-stack, type safe Tanstack dashboard with Clerk auth, tRPC, Shadcn and the full Tanstack suite (tanstack: query, form, table, file router).

Demo of app and UI here: **[Beta-Dash Demo](https://tanstack-forge-starter.vercel.app/)**

## ✨ Tech Stack

- 🚦 **[TanStack Router](https://tanstack.com/router)** - Type-safe file-based routing with loaders and actions
- 🔄 **[TanStack Query](https://tanstack.com/query)** - Data fetching and caching
- 📝 **[TanStack Form](https://tanstack.com/form)** - Powerful form management 
- 📊 **[TanStack Table](https://tanstack.com/table)** - Headless UI for building data tables
- 🔒 **[Clerk](https://clerk.com/docs)** - Modern authentication with development mode support
- 🔌 **[tRPC](https://trpc.io/docs)** - End-to-end type-safe APIs
- 💾 **[Prisma ORM](https://www.prisma.io/docs/orm)** with **MongoDB** - Type-safe database access
- 🎨 **[Shadcn UI](https://ui.shadcn.com/docs)** with **[Tailwind CSS](https://tailwindcss.com/)** - Beautiful UI components
- ⚡ **[Vite](https://v5.vite.dev/guide)** - Lightning fast development

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher)
- [pnpm](https://pnpm.io/) (recommended) or npm/yarn
- MongoDB instance (see [Database Setup](#database-setup))
- Clerk account (see [Authentication Setup](#authentication-setup))

### Installation

1. Clone the repository:

```sh
git clone https://github.com/GoDjMike/beta-dash.git
cd tanstack-forge
```

2. Install dependencies:

```sh
pnpm install
```

3. Set up environment variables by creating a `.env` file in the root directory:

```env
# Database
DATABASE_URL="mongodb://mongo:<mongokey>@metro.proxy.rlwy.net:53250"

# Clerk Authentication
VITE_CLERK_PUBLISHABLE_KEY=pk_test_********************
CLERK_SECRET_KEY=sk_test_********************

# Development Mode true bypasses Clerk authentication check and uses devAuth
VITE_DEV_MODE=true
```

4. Push the database schema to your MongoDB instance:

```sh
pnpm prisma db push
```

5. Start the development server:

```sh
pnpm dev
```

6. Open [http://localhost:5173](http://localhost:5173) in your browser.

## 🔧 Project Structure

```
tanstack-forge/
├── prisma/                # Database schema and migrations
│   └── schema.prisma     # Prisma schema definition
├── public/               # Static assets
├── src/
│   ├── api/              # External API routes
│   ├── components/       # UI components
│   │   ├── auth/        # Authentication components
│   │   ├── common/      # Shared components
│   │   ├── features/    # Feature-specific components
│   │   │   ├── posts/   # Post feature components
│   │   │   ├── users/   # User feature components
│   │   │   └── ...      # Other feature components
│   │   ├── layouts/     # Layout components
│   │   └── ui/          # Shadcn UI components
│   ├── hooks/           # Custom React hooks
│   ├── lib/             # Utility functions and constants
│   │   ├── constants.ts # Application constants
│   │   ├── prisma.ts    # Prisma client
│   │   ├── trpc.ts      # tRPC setup
│   │   └── utils.ts     # Utility functions
│   ├── pages/           # Page components
│   │   ├── about.tsx    # About page route
│   │   ├── examples.tsx    # Examples page route
│   │   └── features.tsx    # Features page route
│   ├── providers/       # React context providers
│   │   ├── auth-provider.tsx    # Authentication provider
│   │   └── trpc-provider.tsx    # tRPC provider
│   ├── routes/          # File-based routing
│   │   ├── __root.tsx   # Root layout and providers
│   │   ├── index.tsx    # Home page route (used for the features page in this starter)
│   │   ├── about.tsx    # About page route
│   │   └── examples.tsx    # Examples page route
│   ├── server/          # Backend logic
│   │   ├── context.ts   # tRPC context
│   │   ├── router.ts    # Base router setup
│   │   └── routers/     # Route handlers
│   │       ├── _app.ts  # Root router
│   │       ├── post.router.ts
│   │       └── user.router.ts
│   ├── types/           # TypeScript type definitions
│   │   ├── api.types.ts       # API types
│   │   ├── auth.types.ts      # Authentication types
│   │   ├── common.types.ts    # Common types
│   │   ├── form.types.ts      # Form types
│   │   ├── post.types.ts      # Post types
│   │   ├── router.types.ts    # Router types
│   │   ├── table.types.ts     # Table types
│   │   └── user.types.ts      # User types
│   ├── index.css        # Global CSS and Tailwind imports
│   ├── routeTree.gen.ts # Route tree generator (generated from TanStack Router)
│   └── main.tsx         # Application entry point
├── .env                 # Environment variables
├── .env.example         # Example environment variables
├── .gitignore           # Git ignore rules
├── index.html           # HTML template
├── package.json         # Project dependencies
├── tailwind.config.js   # Tailwind configuration
├── tsconfig.json        # TypeScript configuration
└── vite.config.ts      # Vite configuration
```

## 🎨 Color Scheme and Styling

Beta-Dash uses a sophisticated color system defined in `src/index.css`:

```css
:root {
  /* Main brand colors */
  --color-primary: 263.4 70% 50.4%;    /* Purple */
  --color-secondary: 215 27.9% 16.9%;  /* Dark blue-gray */
  --color-accent: 215 27.9% 16.9%;     /* Accent color */
  
  /* Semantic colors */
  --color-success: 142 72% 29%;    /* Green */
  --color-warning: 38 92% 50%;     /* Yellow/Amber */
  --color-error: 0 62.8% 30.6%;    /* Red */
  --color-info: 199 89% 48%;       /* Blue */
  
  /* Base colors - Dark theme by default */
  --background: 224 71.4% 4.1%;
  --foreground: 210 20% 98%;
  
  /* Component colors */
  --card: 224 71.4% 4.1%;
  --card-foreground: 210 20% 98%;
  --popover: 224 71.4% 4.1%;
  --popover-foreground: 210 20% 98%;
  /* ... and more component-specific colors */
}
```

### Theme Features:

- **HSL Color Format**: All colors are defined in HSL format for easy manipulation
- **CSS Variables**: Enables dynamic theme switching and component-specific styling
- **Semantic Colors**: Clear naming conventions for different UI states
- **Dark Mode Ready**: Built-in dark mode support
- **Component-Specific Colors**: Dedicated variables for different UI components

## 🛣️ Routing with TanStack Router

Beta-Dash uses TanStack Router's file-based routing system:

```
src/routes/
├── __root.tsx           # Root layout and providers
├── index.tsx           # Home page (/)
├── about.tsx           # About page (/about)
└── examples/
    └── index.tsx       # Examples page (/examples)
```

### Route Configuration

Routes are automatically generated from the file structure:

```typescript
// src/routes/__root.tsx
export const Route = createRootRoute({
  component: () => (
    <AuthContextProvider>
      <RootLayout>
        <Outlet />
      </RootLayout>
    </AuthContextProvider>
  ),
});

// src/routes/index.tsx
export const Route = createFileRoute('/')({
  component: HomePage,
});
```

## 🔐 Authentication

Beta-Dash supports two authentication modes:

### Development Mode

When `VITE_DEV_MODE=true`:
- Uses a simplified authentication flow
- No external auth service required
- Perfect for development and testing

### Production Mode

When `VITE_DEV_MODE=false`:
- Uses Clerk for secure authentication
- Supports email/password and social logins
- Full user management features

When enabled, development mode:

- Shows debugging information and devtools
- Enables more detailed error messages
- Makes tRPC panel accessible
- Displays TanStack Query and Router devtools
- Bypasses certain authentication checks for faster development

Set to `false` for production-like behavior during development.

## 🗄️ API Structure

The backend API is organized using tRPC routers:

```
src/server/
├── context.ts          # Request context
├── router.ts           # Base router setup
└── routers/
    ├── _app.ts        # Root router
    ├── post.router.ts # Post-related endpoints
    └── user.router.ts # User-related endpoints
```

### Example Router:

```typescript
// src/server/routers/user.router.ts
export const userRouter = router({
  list: publicProcedure
    .query(({ ctx }) => ctx.prisma.user.findMany()),
  
  byId: protectedProcedure
    .input(z.string())
    .query(({ ctx, input }) => ctx.prisma.user.findUnique({
      where: { id: input }
    })),
});
```

## 🔌 tRPC Integration

Beta-Dash provides a seamless integration between tRPC, TanStack Router, and TanStack Query for end-to-end type safety.

### Base Setup
```typescript
// src/server/router.ts
const t = initTRPC.context<Context>().create();
export const router = t.router;
export const publicProcedure = t.procedure;
export const protectedProcedure = t.procedure.use(({ ctx, next }) => {
  if (!ctx.auth?.userId) {
    throw new TRPCError({ code: 'UNAUTHORIZED' });
  }
  return next({
    ctx: { auth: ctx.auth },
  });
});
```

### Router Implementation
```typescript
// src/server/routers/user.router.ts
export const userRouter = router({
  me: protectedProcedure
    .query(({ ctx }) => ctx.prisma.user.findUnique({
      where: { clerkId: ctx.auth.userId },
    })),

  updateProfile: protectedProcedure
    .input(z.object({
      name: z.string().min(2).max(50).optional(),
      role: z.nativeEnum(UserRole).optional(),
    }))
    .mutation(({ ctx, input }) => ctx.prisma.user.update({
      where: { clerkId: ctx.auth.userId },
      data: input,
    })),
});
```

### TanStack Router Integration
```typescript
// src/routes/user.tsx
export const Route = createFileRoute('/user')({
  loader: () => trpc.user.me.ensureData(),
  component: UserProfile,
});
```

### TanStack Query Usage
```typescript
// In your React components
function UserProfile() {
  // Automatic type inference from your tRPC router
  const { data: user } = api.user.me.useQuery();
  const utils = api.useUtils();
  
  const { mutate: updateProfile } = api.user.updateProfile.useMutation({
    onSuccess: () => {
      // Invalidate and refetch
      utils.user.me.invalidate();
    },
  });

  return (/* ... */);
}
```

## 📝 Type System

Beta-Dash emphasizes type safety across the entire stack:

### Constants and Enums

Store application constants and enums in `src/lib/constants.ts`:

```typescript
// src/lib/constants.ts
export const APP_NAME = "Beta-Dash";

export enum UserRole {
  ADMIN = "ADMIN",
  USER = "USER",
}

export enum UserStatus {
  ACTIVE = "ACTIVE",
  INACTIVE = "INACTIVE",
}

// Feature flags
export const FEATURES = {
  DARK_MODE: true,
  ANALYTICS: false,
};
```

### Type Definitions

Store shared type definitions in the `src/types` folder:

```typescript
// src/types/common.ts
export type Status = 'idle' | 'loading' | 'success' | 'error';

export interface PaginationParams {
  page: number;
  limit: number;
}

export interface ApiResponse<T> {
  data: T;
  status: Status;
  error?: string;
}
```

### End-to-End Type Safety

Beta-Dash provides end-to-end type safety through:

1. **Prisma Schema to TypeScript**:
   ```prisma
   // prisma/schema.prisma
   model User {
     id        String   @id @default(auto()) @map("_id") @db.ObjectId
     clerkId   String   @unique
     name      String?
     email     String   @unique
     role      String   @default("USER")
     status    String   @default("ACTIVE")
     createdAt DateTime @default(now())
     updatedAt DateTime @updatedAt
   }
   ```

2. **tRPC with Zod Validation**:
   ```typescript
   // src/server/routers/user.router.ts
   const userUpdateSchema = z.object({
     name: z.string().min(2).max(50).optional(),
     role: z.nativeEnum(UserRole).optional(),
   });

   export const userRouter = router({
     updateProfile: protectedProcedure
       .input(userUpdateSchema)
       .mutation(async ({ ctx, input }) => {
         return ctx.prisma.user.update({
           where: { clerkId: ctx.auth.userId },
           data: input,
         });
       }),
   });
   ```

## 🔄 Data Flow

Beta-Dash implements a clean and type-safe data flow:

1. **Database Layer** (Prisma with MongoDB)
   - Models defined in `prisma/schema.prisma`
   - Type-safe database queries via Prisma Client

2. **API Layer** (tRPC)
   - Route handlers in `src/server/routers/`
   - Input validation with Zod
   - Business logic processing
   - Type-safe responses

3. **Client Layer** (TanStack Query + tRPC)
   - Auto-generated hooks from tRPC procedures
   - Automatic cache management
   - Optimistic updates
   - Type-safe mutations

4. **UI Layer** (React + Shadcn UI)
   - Type-safe props and state
   - Strongly typed event handlers
   - Component composition with TypeScript

## 🧪 Testing

Beta-Dash includes a comprehensive testing setup:

### Unit Tests
```typescript
// src/__tests__/utils.test.ts
import { describe, it, expect } from 'vitest';
import { formatDate } from '@/lib/utils';

describe('utils', () => {
  it('formats date correctly', () => {
    const date = new Date('2024-01-01');
    expect(formatDate(date)).toBe('Jan 1, 2024');
  });
});
```

### Component Tests
```typescript
// src/__tests__/components/Button.test.tsx
import { render, screen } from '@testing-library/react';
import { Button } from '@/components/ui/button';

describe('Button', () => {
  it('renders correctly', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeInTheDocument();
  });
});
```

### API Tests
```typescript
// src/__tests__/api/user.test.ts
import { createInnerTRPCContext } from '@/server/context';
import { appRouter } from '@/server/routers/_app';

describe('User API', () => {
  it('returns user profile', async () => {
    const ctx = createInnerTRPCContext({ auth: mockAuth });
    const caller = appRouter.createCaller(ctx);
    const result = await caller.user.me();
    expect(result).toHaveProperty('id');
  });
});
```

Run tests with:
```sh
pnpm test        # Run all tests
pnpm test:watch  # Run tests in watch mode
pnpm test:ui     # Run tests with UI
pnpm test:coverage # Run tests with coverage report
```

## 📚 Resources

- [TanStack Router Documentation](https://tanstack.com/router/latest/docs/framework/react/overview)
- [TanStack Query Documentation](https://tanstack.com/query/latest/docs/react/overview)
- [tRPC Documentation](https://trpc.io/docs)
- [Prisma Documentation](https://www.prisma.io/docs)
- [Clerk Documentation](https://clerk.com/docs)
- [Shadcn UI Documentation](https://ui.shadcn.com/docs)
