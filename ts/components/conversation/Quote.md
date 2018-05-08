### With a quotation, text-only replies

#### Plain text

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'About six',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### With emoji

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'About 🔥six🔥',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many 🔥ferrets🔥 do you have? ',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Replies to you or yourself

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'About six',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: util.ourNumber,
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: util.ourNumber,
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### In a group conversation

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'About six',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550010',
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550007',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550002',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme} type="group">
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### A lot of text in quotation

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Woo, otters!',
  sent_at: Date.now() - 18000000,
  quote: {
    text:
      'I have lots of things to say. First, I enjoy otters. Second best are cats. ' +
      'After that, probably dogs. And then, you know, reptiles of all types. ' +
      'Then birds. They are dinosaurs, after all. Then cephalapods, because they are ' +
      'really smart.',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### A lot of text in quotation, with icon

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Woo, otters!',
  sent_at: Date.now() - 18000000,
  quote: {
    text:
      'I have lots of things to say. First, I enjoy otters. Second best are cats. ' +
      'After that, probably dogs. And then, you know, reptiles of all types. ' +
      'Then birds. They are dinosaurs, after all. Then cephalapods, because they are ' +
      'really smart.',
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'text/plain',
        fileName: 'lorum_ipsum.txt',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### A lot of text in quotation, with image

```jsx
const thumbnail = {
  objectUrl: util.gifObjectUrl,
};
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Woo, otters!',
  sent_at: Date.now() - 18000000,
  quote: {
    text:
      'I have lots of things to say. First, I enjoy otters. Second best are cats. ' +
      'After that, probably dogs. And then, you know, reptiles of all types. ' +
      'Then birds. They are dinosaurs, after all. Then cephalapods, because they are ' +
      'really smart.',
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'image/gif',
        fileName: 'pi.gif',
        thumbnail: {
          contentType: 'image/gif',
        },
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

outgoing.quoteThumbnail = thumbnail;
incoming.quoteThumbnail = thumbnail;

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Image with caption

```jsx
const thumbnail = {
  objectUrl: util.gifObjectUrl,
  id: '3234-23423-2342',
};
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: "Totally, it's a pretty unintuitive concept.",
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'I am pretty confused about Pi.',
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'image/gif',
        fileName: 'pi.gif',
        thumbnail: {
          contentType: 'image/gif',
        },
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

outgoing.quoteThumbnail = thumbnail;
incoming.quoteThumbnail = thumbnail;

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Image

```jsx
const thumbnail = {
  objectUrl: util.gifObjectUrl,
};

const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Yeah, pi. Tough to wrap your head around.',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'image/gif',
        fileName: 'pi.gif',
        thumbnail: {
          contentType: 'image/gif',
        },
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

outgoing.quoteThumbnail = thumbnail;
incoming.quoteThumbnail = thumbnail;

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Image with no thumbnail

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Yeah, pi. Tough to wrap your head around.',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'image/gif',
        fileName: 'pi.gif',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Video with caption

```jsx
const thumbnail = {
  objectUrl: util.gifObjectUrl,
};

const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Sweet the way the video sneaks up on you!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    text: 'Check out this video I found!',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'video/mp4',
        fileName: 'freezing_bubble.mp4',
        thumbnail: {
          contentType: 'image/gif',
        },
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

outgoing.quoteThumbnail = thumbnail;
incoming.quoteThumbnail = thumbnail;

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Video

```jsx
const thumbnail = {
  objectUrl: util.gifObjectUrl,
};

const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Awesome!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'video/mp4',
        fileName: 'freezing_bubble.mp4',
        thumbnail: {
          contentType: 'image/gif',
          data: util.gif,
        },
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

outgoing.quoteThumbnail = thumbnail;
incoming.quoteThumbnail = thumbnail;

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Video with no thumbnail

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Awesome!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'video/mp4',
        fileName: 'freezing_bubble.mp4',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);

const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Audio with caption

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'I really like it!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    text: 'Check out this beautiful song!',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'audio/mp3',
        fileName: 'agnus_dei.mp4',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Audio

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'I really like it!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'audio/mp3',
        fileName: 'agnus_dei.mp4',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Voice message

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'I really like it!',
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        // proposed as of afternoon of 4/6 in Quoted Replies group
        flags: textsecure.protobuf.AttachmentPointer.Flags.VOICE_MESSAGE,
        contentType: 'audio/mp3',
        fileName: 'agnus_dei.mp4',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Other file type with caption

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: "I can't read latin.",
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    text: 'This is my manifesto. Tell me what you think!',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'text/plain',
        fileName: 'lorum_ipsum.txt',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Other file type

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: "Sorry, I can't read latin!",
  sent_at: Date.now() - 18000000,
  quote: {
    author: '+12025550011',
    id: Date.now() - 1000,
    attachments: [
      {
        contentType: 'text/plain',
        fileName: 'lorum_ipsum.txt',
      },
    ],
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

### With a quotation, including attachment

#### Quote, image attachment, and caption

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  body: 'Like pi or so?',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.gif,
      fileName: 'pi.gif',
      contentType: 'image/gif',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, image attachment

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.gif,
      fileName: 'pi.gif',
      contentType: 'image/gif',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, portrait image attachment

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.portraitYellow,
      fileName: 'pi.gif',
      contentType: 'image/gif',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, video attachment

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.mp4,
      fileName: 'freezing_bubble.mp4',
      contentType: 'video/mp4',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, audio attachment

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.mp3,
      fileName: 'agnus_dei.mp3',
      contentType: 'audio/mp3',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, file attachment

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
  attachments: [
    {
      data: util.txt,
      fileName: 'lorum_ipsum.txt',
      contentType: 'text/plain',
    },
  ],
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

#### Quote, but no message

```jsx
const outgoing = new Whisper.Message({
  type: 'outgoing',
  sent_at: Date.now() - 18000000,
  quote: {
    text: 'How many ferrets do you have?',
    author: '+12025550011',
    id: Date.now() - 1000,
  },
});
const incoming = new Whisper.Message(
  Object.assign({}, outgoing.attributes, {
    source: '+12025550011',
    type: 'incoming',
    quote: Object.assign({}, outgoing.attributes.quote, {
      author: '+12025550005',
    }),
  })
);
const View = Whisper.MessageView;
<util.ConversationContext theme={util.theme}>
  <util.BackboneWrapper View={View} options={{ model: incoming }} />
  <util.BackboneWrapper View={View} options={{ model: outgoing }} />
</util.ConversationContext>;
```

### In bottom bar

#### Plain text

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      i18n={window.i18n}
    />
  </div>
</div>
```

#### With an icon

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      i18n={window.i18n}
      attachments={[
        {
          contentType: 'image/jpeg',
          fileName: 'llama.jpg',
        },
      ]}
    />
  </div>
</div>
```

#### With an image

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      i18n={window.i18n}
      attachments={[
        {
          contentType: 'image/gif',
          fileName: 'llama.gif',
          thumbnail: {
            objectUrl: util.gifObjectUrl,
          },
        },
      ]}
    />
  </div>
</div>
```

#### With a close button

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      onClose={() => console.log('Close was clicked!')}
      i18n={window.i18n}
    />
  </div>
</div>
```

#### With a close button and icon

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      onClose={() => console.log('Close was clicked!')}
      i18n={window.i18n}
      attachments={[
        {
          contentType: 'image/jpeg',
          fileName: 'llama.jpg',
        },
      ]}
    />
  </div>
</div>
```

#### With a close button and image

```jsx
<div className={util.theme}>
  <div className="bottom-bar">
    <Quote
      text="How many ferrets do you have?"
      authorColor="blue"
      authorTitle={util.ourNumber}
      authorProfileName="Mr. Blue"
      id={Date.now() - 1000}
      onClose={() => console.log('Close was clicked!')}
      i18n={window.i18n}
      attachments={[
        {
          contentType: 'image/gif',
          fileName: 'llama.gif',
          thumbnail: {
            objectUrl: util.gifObjectUrl,
          },
        },
      ]}
    />
  </div>
</div>
```
