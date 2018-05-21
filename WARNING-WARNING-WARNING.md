# Why The Fork ?

Because I could not find a working solution for terraform/PHPIPAM.

(And I'm also still trying to figure out the way GO interacts with GitHub)

So, to help anyone that follows down this rabbit hole:

Chris Marchesi (https://github.com/vancluever) created two projects in GitHub (Hi Chris, please correct me if I'm wrong):
- https://github.com/paybyphone/phpipam-sdk-go (A GO DSK for PHPIPAM)
- https://github.com/paybyphone/terraform-provider-phpipam (A Terraform provider for PHPIPAM, which depends on the previous project to actually talk to PHPIPAM)

From what I could gather:
- both of them worked with PHPIPAM 1.2.
- PHPIPAM 1.3 changed the way custom fields are created (it now prepends "custom_" to the field name).
- PHPIPAM has released 1.3.1 and is gearing up for 1.3.2
- Other salient issues: The PHPIPAM rest API returns JSON-Lookalike results but:
  - On a boolean field, it uses an integer (0,1) where it was supposed to return one of two strings ("true" or "false").
  - Said boolean field has been witnessed to return 4, with a meaning of "true".
- Chris left paybyphone and is now working for Hashicorp.  The paybyphone projects are there, but not updated to work with PHPIPAM.
- Some (fortunately few) people have forked those projects, but I couldn't get a single one to pass testacc.  No doubt I'm missing some details.

I've chosen to fork Thanh Nguyen (https://github.com/uthng) as he seems to be making some progress.

The fork trees:
- paybyphone/phpipam-sdk-go
  - myENA/phpipam-sdk-go
  - uthng/phpipam-sdk-go
    - pinacoelho/phpipam-sdk-go

- paybyphone/terraform-provider-phpipam
  - malik-muratovic/terraform-provider-phpipam
  - uthng/terraform-provider-phpipam
  
  
Things that should be done in parallel:
- A script to standup a phpipam testacc instance (probably in docker, on the local machine)
