## About Builds

The fundamental difference between traditional WordPress sites and ones using a static site generator is the way pages are generated. Like mentioned in the [overview](README.md), sites that use this static site generator have to **pre-build** pages from the content that you write in the WordPress backend. Pages are not built when you navigate to them anymore, they are pre-built and thus **static**.

This means that changes you make will not be reflected by the site immediately, as they have to be built. While daunting, this new build process does not change things as much as you might fear. It is important, however, to understand the build process, how safe it is, and how you will interact with it when editing content.

## Triggering Builds

Every time content is changed, the site will have to be rebuilt to reflect the new changes. Sites are set to **automatically rebuild** after the following actions:

- Editing a page (content, fields or anything else on a page)
- Editing a blog post
- Moving a page/post to `private`, `published` or `trash`
- Editing custom fields in the options page (often labeled Esquire Digital, or formerly, NextLevel)
- Changing a post's categories or tags
- Changing a category's information
- Menu changes

Sometimes it's necessary to trigger a build manually. You can easily trigger a build and deploy a site manually by hitting the `Deploy Website` button in the admin bar:

![Deploy Button](/_media/deploying.png)

## Build Statuses

Unlike normal WordPress sites, you cannot instantly see your changes live; they take some time to build. To make things easier, a build status badge is located in the top right of the admin bar, right next to the `Deploy Website` button. The status badge will **automatically update** when the status changes, no reload of the page is required. There are four statuses:

![Build Statuses](https://d33wubrfki0l68.cloudfront.net/9ea344517c2d7c51cc8c0329e969880359f4e00f/e7c74/images/monitor-sites-status-badges@2x.png)

- **Success** - A previous build has successfully concluded and has been **published**. Any changes made should be live.

- **Building** - A build has been triggered and is currently underway. During this time, edits that were made before the current build will not be visible on the website, as the pages are being rebuilt. Builds can take anywhere between under a minute, and up to 10 minutes.

- **Canceled** - A build has been canceled. This can only be done by a developer, and likely indicates a developer is currently working on the site. It is best to confer with a developer about the reason for a `canceled` status before triggering any new builds.

- **Failed** - A bug or intentional safeguard has caused the most recent build to fail. When this happens, subsequent builds will almost undoubtedly fail as well. If you see a failed status, contact a developer to resolve the issue. While the build has failed, the site is still live, just without the changes made since the last successful build.

When you edit a page or perform another edit that automatically triggers build, you will see the badge flip from `Success` to `Building`. When that build finishes and the changes are published, that badge will go back to saying `Success`, and you know that your changes are ready to be viewed.

## Limiting Build Volume

It's important to keep track of what actions will trigger builds, and only trigger them when you need to. Our host for static sites, [Netlify](https://www.netlify.com), bills based on the **total minutes spent building sites**. There's no reason to worry; we have plenty of leeway and build overages won't break any part of the process. However, if we do exceed our allotted build minutes, the business will be charged overage fees.

Also, actions are performed that improve the SEO of the site after each successful build. One of these involves submitting the sitemap to Google, which may get timed out if you trigger many builds in rapid succession.

What **not to do** about limiting your build volume:

- **Do not wait to make small edits**. The generator is built to handle these small edits very quickly. Don't be afraid to trigger a build because you think the edit may be too small.

- **Do not worry about total build volume across sites**. If we have to make a lot of edits across sites, do not worry about overages. If we truly go over our quota because we have to make edits, then that is a valid reason to go over the quota and shouldn't be avoided.

- **Do not worry about breaking anything**. This system is designed to be robust to error. Edits to content should never cause an issue, and if they do, that is a developer's issue. A change that breaks a build will never be published, so do not be scared of breaking anything. In fact, your chances of breaking a site with a content edit are _much less_ with a headless setup!

What **you should do** to limit your build volume:

- **Be sure of the edit before pressing save**. Limiting the amount of _oops_ edits or spelling fixes will eliminate a lot of wasted build time. Remember, whether the edit is a whole page or just one word on the page, it still must be rebuilt, and will take the same amount of time.

- **Use the `Deploy Site` button sparingly**. The `Deploy Site` button should only be used when the build status is `Succesful` and you don't see your changes live. Think of it as the same thing as clearing the cache to try and see why your changes aren't displaying.
