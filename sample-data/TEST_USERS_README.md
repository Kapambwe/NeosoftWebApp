# Test Users for Development and Testing

This file contains predefined test users for development and testing purposes. These users can be used to test different roles and permissions in the application.

## Available Test Users

### Administrative Users

#### Super Administrator
- **Username:** `superadmin`
- **Password:** `super123`
- **Roles:** SuperUser, Administrator, Manager
- **2FA Required:** Yes
- **Description:** Full system access with all permissions
- **Use Case:** Testing all system features, security configurations

#### System Administrator
- **Username:** `admin`
- **Password:** `admin123`
- **Roles:** Administrator, SuperUser
- **2FA Required:** No
- **Description:** Standard administrator with full access
- **Use Case:** General administration tasks, user management

### Management & Finance

#### Manager
- **Username:** `manager`
- **Password:** `manager123`
- **Roles:** Manager, User
- **2FA Required:** No
- **Description:** Department manager with team oversight
- **Use Case:** Testing manager-level permissions, team management

#### Accountant
- **Username:** `accountant`
- **Password:** `acc123`
- **Roles:** Accountant, User
- **2FA Required:** Yes
- **Description:** Financial data access and reporting
- **Use Case:** Testing financial features, commission calculations, tax management

#### HR Administrator
- **Username:** `hr.admin`
- **Password:** `hr123`
- **Roles:** HRAdmin, User
- **2FA Required:** Yes
- **Description:** Human resources management
- **Use Case:** Testing employee management, payroll, equity grants

#### Auditor
- **Username:** `auditor`
- **Password:** `audit123`
- **Roles:** Auditor, User
- **2FA Required:** Yes
- **Description:** Read-only access to all data with audit capabilities
- **Use Case:** Testing audit logs, compliance features, reporting

### Technical Users

#### Developer
- **Username:** `developer`
- **Password:** `dev123`
- **Roles:** Developer, User
- **2FA Required:** No
- **Description:** Development and deployment access
- **Use Case:** Testing application management, logs, metrics

### Business Users

#### Affiliate Manager
- **Username:** `affiliate.manager`
- **Password:** `aff123`
- **Roles:** AffiliateManager, User
- **2FA Required:** No
- **Description:** Manages affiliates, resellers, and partners
- **Use Case:** Testing affiliate management, commission approvals, link management

#### Sales Representative
- **Username:** `sales.rep`
- **Password:** `sales123`
- **Roles:** SalesRep, User
- **2FA Required:** No
- **Description:** Customer and opportunity management
- **Use Case:** Testing sales features, customer creation, opportunities

#### Support Agent
- **Username:** `support`
- **Password:** `support123`
- **Roles:** Support, User
- **2FA Required:** No
- **Description:** Customer support and ticket management
- **Use Case:** Testing support tickets, incidents, customer service features

### External Users (Affiliates)

#### Influencer
- **Username:** `influencer`
- **Password:** `inf123`
- **Roles:** Influencer, Affiliate
- **2FA Required:** No
- **Description:** Social media influencer affiliate
- **Use Case:** Testing influencer portal, link generation, commission viewing
- **Limited Permissions:** Own data only, no customer registration

#### Reseller
- **Username:** `reseller`
- **Password:** `res123`
- **Roles:** Reseller, Affiliate
- **2FA Required:** No
- **Description:** Product reseller with customer registration
- **Use Case:** Testing reseller portal, customer registration, link management
- **Special Features:** Can register customers directly

#### Partner
- **Username:** `partner`
- **Password:** `partner123`
- **Roles:** Partner, Affiliate
- **2FA Required:** No
- **Description:** Strategic partner with highest affiliate privileges
- **Use Case:** Testing partner portal, sub-affiliate management, advanced features
- **Special Features:** Can manage sub-affiliates, access partner resources

### Limited Access Users

#### Read-Only User
- **Username:** `readonly`
- **Password:** `read123`
- **Roles:** ReadOnly, User
- **2FA Required:** No
- **Description:** View-only access to public and own data
- **Use Case:** Testing permission restrictions, view-only scenarios

#### Disabled User (Testing)
- **Username:** `disabled.user`
- **Password:** `disabled123`
- **Roles:** User
- **2FA Required:** No
- **Active:** No
- **Description:** Disabled account for testing access restrictions
- **Use Case:** Testing account deactivation, login restrictions

## Quick Reference Table

| Username | Password | Main Role | 2FA | Use For |
|----------|----------|-----------|-----|---------|
| superadmin | super123 | SuperUser | ✓ | Full system access |
| admin | admin123 | Administrator | ✗ | Standard admin tasks |
| manager | manager123 | Manager | ✗ | Team management |
| accountant | acc123 | Accountant | ✓ | Financial operations |
| hr.admin | hr123 | HRAdmin | ✓ | HR management |
| auditor | audit123 | Auditor | ✓ | Compliance & auditing |
| developer | dev123 | Developer | ✗ | Technical features |
| affiliate.manager | aff123 | AffiliateManager | ✗ | Affiliate management |
| sales.rep | sales123 | SalesRep | ✗ | Sales features |
| support | support123 | Support | ✗ | Customer support |
| influencer | inf123 | Influencer | ✗ | Influencer portal |
| reseller | res123 | Reseller | ✗ | Reseller portal |
| partner | partner123 | Partner | ✗ | Partner portal |
| readonly | read123 | ReadOnly | ✗ | Limited access |
| disabled.user | disabled123 | User | ✗ | Account disabled |

## Permission Categories

### Affiliate Types Comparison

| Feature | Influencer | Reseller | Partner |
|---------|-----------|----------|---------|
| View own commissions | ✓ | ✓ | ✓ |
| Generate affiliate links | ✓ | ✓ | ✓ |
| View performance | ✓ | ✓ | ✓ |
| Register customers | ✗ | ✓ | ✓ |
| Manage own links | ✗ | ✓ | ✓ |
| Access partner portal | ✗ | ✗ | ✓ |
| Manage sub-affiliates | ✗ | ✗ | ✓ |
| View partner resources | ✗ | ✗ | ✓ |

## Testing Scenarios

### 1. Authentication & Authorization
- Test login with each user type
- Test 2FA flow with users requiring it (superadmin, accountant, hr.admin, auditor)
- Test disabled account cannot login (disabled.user)
- Test role-based access control

### 2. Affiliate Portal Testing
Use these combinations:
- **Influencer:** Limited features, link sharing only
- **Reseller:** Customer registration, link management
- **Partner:** Full features including sub-affiliate management
- **Affiliate Manager:** Backend management of all affiliates

### 3. Financial Operations
- **Accountant:** Test financial reports, tax calculations, commission processing
- **Auditor:** Test read-only access to all financial data
- **Affiliate Manager:** Test commission approvals

### 4. Administrative Tasks
- **Admin/SuperAdmin:** User management, system configuration
- **Manager:** Team management, approval workflows
- **HR Admin:** Employee and equity management

### 5. Permission Boundaries
- **ReadOnly:** Verify cannot edit or delete
- **Developer:** Verify can access technical features but not financial
- **Support:** Verify can access customer data but not financial data

## Security Notes

⚠️ **WARNING:** These are test credentials for development only!

- **DO NOT** use these credentials in production
- **DO NOT** commit production credentials to version control
- All test users have simple passwords for easy testing
- 2FA is enabled for users handling sensitive data
- The disabled.user account should fail login attempts

## Implementation Notes

- Test users are loaded from `wwwroot/sample-data/test-users.json`
- If JSON file is not found, fallback users are created in code
- User IDs are GUIDs for consistency
- Passwords are stored in plain text (test only!)
- In production, use proper password hashing and secure authentication

## Extending Test Users

To add new test users, edit `test-users.json` and include:

```json
{
  "id": "unique-guid",
  "username": "username",
  "password": "password",
  "email": "email@example.com",
  "firstName": "First",
  "lastName": "Last",
  "department": "Department",
  "isActive": true,
  "roles": ["Role1", "Role2"],
  "requiresTwoFactor": false,
  "permissions": ["Permission1", "Permission2"]
}
```

## Related Files

- `Services/Auth/TestAuthenticationService.cs` - Authentication service
- `Services/Auth/IAuthenticationService.cs` - Authentication interface
- `Models/Auth/UserDto.cs` - User data transfer object
- `wwwroot/sample-data/test-users.json` - This user data file

---

**Last Updated:** December 2024
**Purpose:** Development and testing only
**Status:** Active
