# Day 2: Groups and my own policy

I made two groups: `admins` with AdministratorAccess and `ReadOnly` with ReadOnlyAccess. It's easier to give permissions to a group than to each user.

Then I made an S3 bucket in Frankfurt and wrote a policy for it by hand. The part I had to think about: `s3:ListBucket` goes on the bucket itself, but `s3:GetObject` goes on `bucket/*` because it works on the files inside.

I tested it in the Policy Simulator before running it. I guessed right:

- GetObject: allowed
- ListBucket: allowed
- PutObject: denied
- DeleteObject: denied

The last two are denied because I never allowed them. That's the default deny. It also showed me what least privilege means: only give the access that is really needed.
