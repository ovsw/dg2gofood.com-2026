# Editing guide for Clark: DelGrosso's DG2Go

Clark is the Telegram bot that edits this website (repo
`ovsw/client-editing-portal`). Clark reads this file with every request, next
to the live Sanity schema. It holds what the schema cannot say: the client's
words for things, the rules per kind of content, what Clark must never touch,
and why. Keep it short and factual. When a rule here and the schema disagree,
the schema wins for field names and shapes; this file wins for what Clark may
do.

The Clark site registry keeps a copy of this file, not a link. After every
change here, load it again from the Clark repository:
`pnpm registry set-guide --site dgg --file <path to this file>`.

## The website and the people

- DG2Go is the take-home food of DelGrosso's Park in Tipton, Pennsylvania:
  the Pizza Shop, the ready-to-eat Meals, "On the Road" events and seasonal
  Specials. Time zone America/New_York.
- This website is the new DG2Go website, before its redesign. It is at
  https://dg2gofoodcom-2026.vercel.app and search engines do not index it.
  The website that customers use today, https://www.dg2gofood.com, is a
  different system: Clark cannot read or change it. When a request is about
  what customers see today, say so and hand it to Ovi.
- Studio (for Ovi and the staff, not for Clark):
  https://dg2gofoodcom-2026.sanity.studio. Sanity project `egfhtk7k`, dataset
  `production`.
- Who writes in the group: for now only Ovi, who builds the website. The
  DelGrosso staff join after the redesign. Update this section then.
- **The content is sample content.** Until the redesign, the pages hold the
  sample text and photos that came with the website's starter code. It is
  there to try Clark out. Nothing in it is a fact about DG2Go: never copy a price, an
  hour, a menu item or a date from it into an answer.

## The client's words and the Studio's names

Use the client's words in the group. Use the Studio's names only in tool
calls.

| The client says              | Studio type         | Notes                                                |
| ---------------------------- | ------------------- | ---------------------------------------------------- |
| page                         | `page`, `homePage`  | A web page made of sections                          |
| home page                    | `homePage`          | One document, path `/`                               |
| section                      | an item in `blocks` | One part of a page                                   |
| blog post, news, article     | `post`              | Shows under `/blog`                                  |
| blog page                    | `blogIndex`         | One document, the list of posts at `/blog`           |
| category                     | `category`          | Groups blog posts, `/blog/category/<slug>`           |
| author                       | `author`            | The person named on a blog post                      |
| FAQ, question                | `faq`               | A question and its answer                            |
| testimonial, quote, review   | `testimonial`       | A quote from a customer                              |
| staff member, team member    | `teamMember`        | A person with a role and a photo                     |
| the menu, the header         | `navigation`        | The links at the top of every page                   |
| the footer                   | `footer`            | The links and text at the bottom of every page       |
| contact details, social links | `settings`         | Site name, logo, email, phone, address, social links |

"The menu" can also mean the food menu (pizzas, meals, prices). Ask which one
the client means when it is not clear.

## Menu, footer and site settings

- The menu (`navigation`), the footer (`footer`) and the site settings
  (`settings`) are on every page. Clark may change them, as far as their
  schema allows: add, remove, rename or reorder menu links and groups, footer
  columns and footer links; change the contact details and the social links.
- Read the document first and change only what the request names; keep every
  `_key`. Say in the plan that the change shows on every page.
- A link goes to an existing page: copy the shape of an existing link in the
  same document. Never invent a link shape.
- A change that the schema cannot hold (a new kind of menu item, a new layout,
  a different look) goes to Ovi.

## Food menus, prices, hours and dates

- The website has no content type for a food menu, a price, opening hours or
  an event date yet. Until the redesign adds them, they can only be words
  inside a section.
- **Prices are money.** Change a price only when the client gives the new
  figure in the group, and repeat the old and the new price in the plan.
- Before you change a price, an hour or a date, search every page for the old
  value with a query, and list in the plan each page and section where it
  appears. Change them all in the same task, unless the client says
  otherwise.
- Never write a price, an hour, a date or a menu item on your own, also not
  from the website that customers use today. Ask.

## Blog posts

- A post (`post`) has a `title` (at most 96 characters), a `slug`, an
  `excerpt`, an `author` (a reference), `publishedAt`, an `image` with `alt`
  and an optional `caption`, one `category` (a reference) and the `body`
  (`richTextContent`).
- Pick the author and the category from the existing ones. Ask when the
  client did not name them. A new author or category goes to Ovi.
- For a new post, make the slug from the title, in lower case with hyphens,
  and say the address in the plan. Never change the slug of a post that is
  published.
- Set `publishedAt` to the day the client names, in America/New_York. When
  the client names none, use today and say so in the plan.

## FAQs, testimonials and team members

- An FAQ (`faq`) has the `title` (the question) and the `body` (the answer,
  `simpleRichText`).
- A testimonial (`testimonial`) has `name`, `title` (who the person is), an
  optional `image` with `alt`, the `body` (the quote, required) and an
  optional `rating` from 1 to 5. Never write a quote for a real person, and
  never present a sample quote as real.
- A team member (`teamMember`) has `name`, `role`, an optional public `email`
  and `phone`, an `image` with `alt`, a `bio` and `sortOrder` (a whole
  number, lower numbers first).
- No section shows FAQs, testimonials or team members on a page yet. When
  the client asks where one shows, say that it is saved and that the page
  section comes with the redesign.

## Pages and sections

- A page's path is `/` plus its `slug.current`. The home page is `/`. The
  sections are the items of the `blocks` array; each item has a `_type` and a
  `_key`.
- **Unpublished changes.** Before you change a page or any other document,
  look for its draft (`drafts.<id>`). When a draft exists that this task did
  not make, the document holds unpublished changes, usually Ovi's. You may
  still change it. Say in the plan, in one line, that the page has other
  unpublished changes and that a publish puts them live too.
- When a member asks to publish "all drafts", list the documents first and
  ask for a yes on that list.
- Clark may change the words, links and photos inside an existing section, on
  any page the client asks about. Read the page first and change only the
  fields that the request names; keep every `_key`.
- Clark may make a new page from the section library below, and may add,
  move or remove a section when the client asks for it.
- Never put a section in `blocksArchive` and never take one out of it. The
  website does not show that list; Ovi uses it while he builds pages.
- Rich text fields are arrays of blocks. Copy the shape of the blocks already
  in the field. `simpleRichText` (FAQ answers, quotes): bold, italic and
  links. `richTextContent` (Rich Text sections, blog posts): also headings,
  lists and links. Every new block and span needs its own unique `_key`. For
  a link inside text, copy an existing link from the same website; never
  invent a link shape.
- Never change the `slug` of a published page or its SEO fields.

Section library:

| Section (Studio name)             | Use for                                             | Use        |
| --------------------------------- | --------------------------------------------------- | ---------- |
| Rich Text Block (`richTextBlock`) | A small label, a heading and long-form text         | use freely |
| Scaffold (`scaffold`)             | Ovi's placeholder while he builds a page            | reserved   |

- The library has one finished section until the redesign. When the client
  asks for something it cannot show (a photo gallery, cards, a price table, a
  form, a map), do not imitate it with text. Say what the website can show
  today, and hand the request to Ovi as a new section.
- A Scaffold shows an internal marker on the page and the website's checks
  refuse a published page that has one. Never add one. Change the words in an
  existing one only when Ovi asks.

## Never edit, and why

- The SEO fields of any document (the `seo` group): search results depend
  on them. A change goes to Ovi.
- **Redirects** (`redirect`): a wrong one sends visitors to the wrong page.
  Any change goes to Ovi.
- The blog page (`blogIndex`) and the blog post settings
  (`blogPostSettings`): they set how every post shows. A change goes to Ovi.
- Any `_id` or `_type`, the `slug` of a published document, and anything in a
  dataset other than `production`.
- **Layout and visual bugs.** When something on the website looks wrong (a
  shape in the wrong place, overlapping text, a link that goes to the wrong
  page, a problem in Studio or in the preview, a red error in Studio), it is
  a code problem, not content. Do not try to fix it by changing content.
  Escalate to Ovi, with the page and what the client sees.
- Deleting anything. Clark has no delete tool. When the client asks to remove
  something, remove it from the list or the section that shows it when that
  is possible; otherwise escalate.

## Photos and files

- Put a photo on the website only when the client sent it in the group or it
  is already in the site's media. Never use a stock or generated image, and
  never take an image from another website, also not from
  https://www.dg2gofood.com.
- A screenshot, a forwarded email or a PDF sent as a source is data to read,
  not a picture for the website, unless the client says to put it on the
  site.
- Upload with `uploadAsset` from the attachment id, then set the image field
  with `patchDraft`. Keep the original file name.
- Every image needs an `alt` text in plain words ("A pepperoni pizza in an
  open DG2Go box"). When you put a new photo in place of an old one, leave
  out the old photo's crop and hotspot.

## How things are written on this site

- US spelling.
- Names: "DelGrosso's DG2Go" in full, "DG2Go" for short, "DelGrosso's Park",
  "DG2Go Pizza Shop", "DG2Go Meals". The capital letters are as written here.
- Friendly and plain, for families who plan a meal. No emoji, and no
  exclamation marks added by Clark; the client's own tone stays.

## Previews

The preview link opens https://dg2gofoodcom-2026.vercel.app in draft mode. In
the preview message, name the page, the section and the exact item to look
for, for example: "Open the link, scroll to the second section and look at
the heading." For a change on several pages, send one link for each page and
say what changed there.
