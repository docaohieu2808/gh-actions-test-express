# gh-actions-test-express

**Tier:** GitHub Actions L1.5 — fixture dự án thật để stress-test reusable-workflows.

**Vị trí trong learning path:**
```
test-gh-actions (L1) → gh-actions-test-express (L1.5) → reusable-workflows (L5-6)
```

## Mục đích

Fork của [expressjs/express](https://github.com/expressjs/express) dùng làm CI fixture. Lý do dùng Express thay vì repo đồ chơi:

- Test suite thật (~600 tests), lockfile thật → reusable-workflows phải handle real-world Node.js project
- Thừa hưởng upstream workflows SHA-pinned (CodeQL, Scorecard) — minh hoạ best practice supply-chain so sánh với `@master` của reusable-workflows

CI của repo này (`.github/workflows/ci.yml`) gọi thẳng reusable-workflows — tương tự test-gh-actions nhưng với project phức tạp hơn.

## Lưu ý

Đây là **fork để test pipeline**, không phải fork để contribute lại Express. Các workflows upstream (`codeql.yml`, `scorecard.yml`, `legacy.yml`) giữ nguyên để minh hoạ sự khác biệt giữa SHA-pinned actions (chuẩn tốt) và `@master` (learning trade-off).

## Demo points (interview)

- Dùng project thật có test suite đủ lớn để prove pipeline handle được production codebase
- Upstream workflows SHA-pinned (`actions/checkout@v6.0.2 SHA`, `codeql-action@v4.32.4 SHA`) — đây là supply-chain security chuẩn, dùng để giải thích tại sao production nên pin còn `@master` chỉ OK cho learning
