---
layout: post
title:      "Update jsonb Columns Using The Rails Active Record Methods"
date:       2020-02-20 01:54:16 +0000
permalink:  update_jsonb_columns_using_the_rails_active_record_methods
---


While building a Rails API backend for a recent project I came across a challenge when updating jsonb columns.

You see as a pure Rail'ist (Is that a thing...?) I try to stay away from writing *SQL* strings in my app when I could use *Active Record* native methods, but since I had defined some columns as *Jsonb* it seemed like I would need to use *SQL* since all the tutorials were making use of *jsonb_set SQL* method as follows:

```
sql = 'UPDATE users SET preferences = jsonb_set(
options, \'{email_opt_in}\', \'false\', FALSE) WHERE id = 1;'

c.execute(sql)
```

But as a Rail'ist I was looking for something more like `user.update(params)`.

So...
This is what I came up with:
1. First get the current column value which Active Record returns as a Ruby hash:
`user = session_user`
`currentKeys = user.api_keys`

2. Convert *post params* to a hash and extract the nested values which were nested under *keys*:
`hashedParams = user_params.to_h[:keys]`

3. Use the Ruby hash merge method to merge my *post params* and current user column data:
`newKeys = currentKeys.merge(hashedParams)`

4. I could now use the Rails object update method as usual:
`user.update(api_keys: newKeys)`

Here is the complete code:
```
    user = session_user
    currentKeys = user.api_keys
    hashedParams = user_params.to_h[:keys]
    newKeys = currentKeys.merge(hashedParams)

    if user.update(api_keys: newKeys)
        Bla, bla, bla...
```

Ok, now here's the thing: I need validation if the above is acceptable as a Rail'ist(you heard it here first) so please If I'm missing anything(method, convention, irk etc.) comment below :)

Thanks For Reading!

I first published this post on [dev.to](https://dev.to/heshiebee/update-jsonb-columns-using-the-rails-active-record-update-method-2392) before publishing it here.
