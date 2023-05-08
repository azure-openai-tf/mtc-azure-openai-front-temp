<script>
export default {
    name: 'Chatbot',
    data() {
        return {
            participants: [
                {
                    id: 'user1',
                    name: 'Matteo',
                    imageUrl: 'https://avatars3.githubusercontent.com/u/1915989?s=230&v=4'
                },
                {
                    id: 'user2',
                    name: 'Support',
                    imageUrl: 'https://avatars3.githubusercontent.com/u/37018832?s=200&v=4'
                }
            ], // the list of all the participant of the conversation. `name` is the user name, `id` is used to establish the author of a message, `imageUrl` is supposed to be the user avatar.
            titleImageUrl: 'https://a.slack-edge.com/66f9/img/avatars-teams/ava_0001-34.png',
            messageList: [
                { type: 'text', author: `me`, data: { text: `Say yes!` } },
                { type: 'text', author: `user1`, data: { text: `No.` } }
            ], // the list of the messages to show, can be paginated and adjusted dynamically
            newMessagesCount: 0,
            isChatOpen: false, // to determine whether the chat window should be open or closed
            showTypingIndicator: '', // when set to a value matching the participant.id it shows the typing indicator for the specific user
            colors: {
                header: {
                    bg: '#4e8cff',
                    text: '#ffffff'
                },
                launcher: {
                    bg: '#4e8cff'
                },
                messageList: {
                    bg: '#ffffff'
                },
                sentMessage: {
                    bg: '#4e8cff',
                    text: '#ffffff'
                },
                receivedMessage: {
                    bg: '#eaeaea',
                    text: '#222222'
                },
                userInput: {
                    bg: '#f4f7f9',
                    text: '#565867'
                }
            }, // specifies the color scheme for the component
            alwaysScrollToBottom: false, // when set to true always scrolls the chat to the bottom when new events are in (new message, user starts typing...)
            messageStyling: true // enables *bold* /emph/ _underline_ and such (more info at github.com/mattezza/msgdown)
        };
    },
    methods: {
        sendMessage(text) {
            if (text.length > 0) {
                this.newMessagesCount = this.isChatOpen ? this.newMessagesCount : this.newMessagesCount + 1;
                this.onMessageWasSent({ author: 'support', type: 'text', data: { text } });
            }
        },
        onMessageWasSent(message) {
            // called when the user sends a message
            this.messageList = [...this.messageList, message];
        },
        openChat() {
            // called when the user clicks on the fab button to open the chat
            this.isChatOpen = true;
            this.newMessagesCount = 0;
        },
        closeChat() {
            // called when the user clicks on the botton to close the chat
            this.isChatOpen = false;
        },
        handleScrollToTop() {
            // called when the user scrolls message list to top
            // leverage pagination for loading another page of messages
        },
        handleOnType() {
            console.log('Emit typing event');
        },
        editMessage(message) {
            const m = this.messageList.find((m) => m.id === message.id);
            m.isEdited = true;
            m.data.text = message.data.text;
        }
    },
    computed: {
        componentLoader() {
            return this.openChat();
        }
    }
};
</script>

<template>
    <div class="grid grid-nogutter surface-section text-800">
        <div class="card" data-v-856f09a3="">
            <h5 data-v-856f09a3="">ChatGPT 3.5 Turbo</h5>
            <div class="p-timeline p-component p-timeline-alternate p-timeline-vertical customized-timeline" data-v-856f09a3="">
                <div class="p-timeline-event">
                    <div class="p-timeline-event-opposite"></div>
                    <div class="p-timeline-event-separator">
                        <span class="flex w-2rem h-2rem align-items-center justify-content-center text-white border-circle z-1 shadow-2" data-v-856f09a3="" style="background-color: rgb(156, 39, 176)"
                            ><i class="pi pi-shopping-cart" data-v-856f09a3=""></i
                        ></span>
                        <div class="p-timeline-event-connector"></div>
                    </div>
                    <div class="p-timeline-event-content">
                        <div class="p-card p-component" data-v-856f09a3="">
                            <!---->
                            <div class="p-card-body">
                                <div class="p-card-title">Ordered</div>
                                <div class="p-card-subtitle">15/10/2020 10:30</div>
                                <div class="p-card-content">
                                    <img src="/sakai-vue/demo/images/product/game-controller.jpg" width="200" class="shadow-2 mb-3" data-v-856f09a3="" />
                                    <p data-v-856f09a3="">
                                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore sed consequuntur error repudiandae numquam deserunt quisquam repellat libero asperiores earum nam nobis, culpa ratione quam perferendis esse,
                                        cupiditate neque quas!
                                    </p>
                                    <button class="p-button p-component p-button-text" type="button" aria-label="Read more" data-v-856f09a3="">
                                        <!----><!----><span class="p-button-label">Read more</span
                                        ><!----><span class="p-ink" role="presentation" aria-hidden="true"></span>
                                    </button>
                                </div>
                                <!---->
                            </div>
                        </div>
                    </div>
                </div>
                <div class="p-timeline-event">
                    <div class="p-timeline-event-opposite"></div>
                    <div class="p-timeline-event-separator">
                        <span class="flex w-2rem h-2rem align-items-center justify-content-center text-white border-circle z-1 shadow-2" data-v-856f09a3="" style="background-color: rgb(103, 58, 183)"
                            ><i class="pi pi-cog" data-v-856f09a3=""></i
                        ></span>
                        <div class="p-timeline-event-connector"></div>
                    </div>
                    <div class="p-timeline-event-content">
                        <div class="p-card p-component" data-v-856f09a3="">
                            <!---->
                            <div class="p-card-body">
                                <div class="p-card-title">Processing</div>
                                <div class="p-card-subtitle">15/10/2020 14:00</div>
                                <div class="p-card-content">
                                    <!---->
                                    <p data-v-856f09a3="">
                                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore sed consequuntur error repudiandae numquam deserunt quisquam repellat libero asperiores earum nam nobis, culpa ratione quam perferendis esse,
                                        cupiditate neque quas!
                                    </p>
                                    <button class="p-button p-component p-button-text" type="button" aria-label="Read more" data-v-856f09a3="">
                                        <!----><!----><span class="p-button-label">Read more</span
                                        ><!----><span class="p-ink" role="presentation" aria-hidden="true"></span>
                                    </button>
                                </div>
                                <!---->
                            </div>
                        </div>
                    </div>
                </div>
                <div class="p-timeline-event">
                    <div class="p-timeline-event-opposite"></div>
                    <div class="p-timeline-event-separator">
                        <span class="flex w-2rem h-2rem align-items-center justify-content-center text-white border-circle z-1 shadow-2" data-v-856f09a3="" style="background-color: rgb(255, 152, 0)"
                            ><i class="pi pi-envelope" data-v-856f09a3=""></i
                        ></span>
                        <div class="p-timeline-event-connector"></div>
                    </div>
                    <div class="p-timeline-event-content">
                        <div class="p-card p-component" data-v-856f09a3="">
                            <!---->
                            <div class="p-card-body">
                                <div class="p-card-title">Shipped</div>
                                <div class="p-card-subtitle">15/10/2020 16:15</div>
                                <div class="p-card-content">
                                    <!---->
                                    <p data-v-856f09a3="">
                                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore sed consequuntur error repudiandae numquam deserunt quisquam repellat libero asperiores earum nam nobis, culpa ratione quam perferendis esse,
                                        cupiditate neque quas!
                                    </p>
                                    <button class="p-button p-component p-button-text" type="button" aria-label="Read more" data-v-856f09a3="">
                                        <!----><!----><span class="p-button-label">Read more</span
                                        ><!----><span class="p-ink" role="presentation" aria-hidden="true"></span>
                                    </button>
                                </div>
                                <!---->
                            </div>
                        </div>
                    </div>
                </div>
                <div class="p-timeline-event">
                    <div class="p-timeline-event-opposite"></div>
                    <div class="p-timeline-event-separator">
                        <span class="flex w-2rem h-2rem align-items-center justify-content-center text-white border-circle z-1 shadow-2" data-v-856f09a3="" style="background-color: rgb(96, 125, 139)"
                            ><i class="pi pi-check" data-v-856f09a3=""></i></span
                        ><!---->
                    </div>
                    <div class="p-timeline-event-content">
                        <div class="p-card p-component" data-v-856f09a3="">
                            <!---->
                            <div class="p-card-body">
                                <div class="p-card-title">Delivered</div>
                                <div class="p-card-subtitle">16/10/2020 10:00</div>
                                <div class="p-card-content">
                                    <!---->
                                    <p data-v-856f09a3="">
                                        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Inventore sed consequuntur error repudiandae numquam deserunt quisquam repellat libero asperiores earum nam nobis, culpa ratione quam perferendis esse,
                                        cupiditate neque quas!
                                    </p>
                                    <button class="p-button p-component p-button-text" type="button" aria-label="Read more" data-v-856f09a3="">
                                        <!----><!----><span class="p-button-label">Read more</span
                                        ><!----><span class="p-ink" role="presentation" aria-hidden="true"></span>
                                    </button>
                                </div>
                                <!---->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="card col-12" style="margin-top: 30px">
        <div class="p-inputgroup">
            <textarea class="p-inputtext p-component" placeholder="Write a Message."></textarea>
            <button class="p-button p-component" type="button" aria-label="Search">
                <!----><!----><span class="p-button-label">Send</span
                ><!----><span class="p-ink" role="presentation" aria-hidden="true"></span>
            </button>
        </div>
    </div>
</template>
